---
layout: default
title: "Jump from Java 7 to Java 8"
---

## {{ page.title }}

После перехода нашей команды на 8-ую java (да, это случилось!), появилась мысль: "а не переписать ли мне некоторые участки кода одного из сервисов, используя новые возможности java 8..".

Допустим, у нас есть некий метод, который на основе списка документов агрегирует общую информацию по ним. Так выглядел бы стиль, к которому все привыкли за столь долгие годы:
<pre><code>public List<Document> getDocumentsStatistics(List<Document> documents)
    final List<Document> documentsStatistics = new ArrayList();
    for (Document document : documents) {
        final List<DocumentHashType> types = new ArrayList<DocumentHashType>();
        for (DocumentHashType type : document.getDocumentType())
            types.add(type);
        DocumentStatistics documentStatistics = 
        	new DocumentStatistics(
                document.getName(),
                document.getLocation(),
                document.getSourceId(),
                types,
                document.getDateCreated());
        documentsStatistics.add(documentStatistics);
    }
    return documentsStatistics;
}
</code></pre>

Этот же метод в новом стиле:
<pre><code>private List<DocumentStatistics> getDocumentsStatistics(Collection<Document> documents) {
   return new ArrayList<DocumentStatistics>(
           documents
               .stream()
               .map(x -> new DocumentStatistics(
                        x.getName(),
                        x.getLocation(),
                        x.getSourceId(),
                        x.getDocumentHashTypes()
                            .stream()
                            .collect(Collectors.toList()),
                        x.getDateCreated()))
               .collect(Collectors.toList()));
</code></pre>

Весьма неплохо. Более кратко, избегаем mutable state.

Идем далее. Необходимо получить группу по ее id. Как делали раньше:
<pre><code>public DocumentGroup getDocumentGroupById(String id) {
        for (Map.Entry<String, DocumentGroup> group:
        	documentGroups.entrySet()) {
            if (group.getValue().getGroupId().getId() == id)
                return group.getValue();
        }
        return null;
    }
</code></pre>

Давайте преобразуем его:
<pre><code>final DocumentGroup documentGroup = 
	service.getKnowledgeBase()
                .getDocumentGroups()
                .stream()
                .filter(x ->
               	  x.getGroupId().getId() == id)
                .findFirst()
                .get();
</code></pre>