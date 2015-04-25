---
layout: default
title: "Jump from Java 7 to Java 8"
---

## {{ page.title }}

After our team moved to java 8 (yes, it happened!), I've got the idea: "If I rewrite some pieces of one service using new powers of Java 8.."

For example, we have some method, which on the base of documents aggregates common imformation according to them. Here's what old style looked like:
<pre><code><span class="java_keyword">public</span> List&lt;Document&gt; getDocumentsStatistics(List&lt;Document&gt; documents)
    <span class="java_keyword">final</span> List&lt;Document&gt; documentsStatistics = <span class="java_keyword">new</span> ArrayList();
    <span class="java_keyword">for</span> (Document document : documents) {
        <span class="java_keyword">final</span> List&lt;DocumentHashType&gt; types = <span class="java_keyword">new</span> ArrayList&lt;DocumentHashType&gt;();
        <span class="java_keyword">for</span> (DocumentHashType type : document.getDocumentType())
            types.add(type);
        DocumentStatistics documentStatistics = 
        	<span class="java_keyword">new</span> DocumentStatistics(
                        document.getName(),
                        document.getLocation(),
                        document.getSourceId(),
                        types,
                        document.getDateCreated());
        documentsStatistics.add(documentStatistics);
    }
    <span class="java_keyword">return</span> documentsStatistics;
}
</code></pre>

This method in new style:
<pre><code><span class="java_keyword">private</span> List&lt;DocumentStatistics&gt; getDocumentsStatistics(Collection&lt;Document&gt; documents) {
   <span class="java_keyword">return new</span> ArrayList&lt;DocumentStatistics&gt;(
           documents
               .stream()
               .map(x -> <span class="java_keyword">new</span> DocumentStatistics(
                        x.getName(),
                        x.getLocation(),
                        x.getSourceId(),
                        x.getDocumentHashTypes()
                            .stream()
                            .collect(Collectors.toList()),
                        x.getDateCreated()))
               .collect(Collectors.toList()));
</code></pre>

Not bad. More briefly, avoid mutable state.

Next, we need take group for id. Early we did it so:
<pre><code><span class="java_keyword">public</span> DocumentGroup getDocumentGroupById(String id) {
        <span class="java_keyword">for</span> (Map.Entry&lt;String, DocumentGroup&gt; group:
        	documentGroups.entrySet()) {
            <span class="java_keyword">if</span> (group.getValue().getGroupId().getId() == id)
                <span class="java_keyword">return</span> group.getValue();
        }
        <span class="java_keyword">return</span> null;
    }
</code></pre>

Let's convert it:
<pre><code><span class="java_keyword">final</span> DocumentGroup documentGroup = 
	service.getKnowledgeBase()
                .getDocumentGroups()
                .stream()
                .filter(x ->
               	  x.getGroupId().getId() == id)
                .findFirst()
                .get();
</code></pre>