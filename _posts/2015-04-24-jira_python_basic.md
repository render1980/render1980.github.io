---
layout: default
title: "Usage JIRA API with Python"
---

## {{ page.title }}

<pre><code><span class="python_keyword">from</span> jira <span class="python_keyword">import</span> JIRA
user = <span class="python_string">"jira_login"</span>
password = <span class="python_string">"jira_password"</span>
jira = JIRA(url, basic_auth=(user, password))
</code></pre>

We can calcualte active tasks total time, which were changed today (for last 8 hours):
<pre><code>updated_today_issues = jira.search_issues(
	'assignee=%s and resolution=%s and updated %s and status in %s order by %s DESC',
	(<span class="python_string">'currentUser()'</span>, <span class="python_string">'Unresolved'</span>, <span class="python_string">'>= -8h'</span>,
	 <span class="python_string">'(Open, "In Progress", Reopened,"Under review")'</span>, <span class="python_string">'updatedDate'</span>))
sum([issue.fields.timespent <span class="python_keyword">for</span> issue <span class="python_keyword">in</span> updated_today_issues])
</code></pre>

It's not suitable: resulting value summarize all time logged for active tasks from the task creation date. Somebody can changed some field of the task, so it affects to 'update time' field.

And how can we take total time for all tasks, logged only today ?

We need take all issues which have been updated today and find total time in worklogs I've updated: 
<pre><code>logged_today_issues = jira.search_issues(
		<span class="python_string">'assignee=%s and updated %s order by %s DESC'</span>,
		(<span class="python_string">'currentUser()'</span>, <span class="python_string">'>= -8h'</span>, <span class="python_string">'updatedDate'</span>))

<span class="python_keyword">for</span> i <span class="python_keyword">in</span> logged_today_issues:
	issue_worklogs = i.fields.worklog.worklogs
	my_today_issue_worklogs = <span class="python_keyword">filter</span>(
		<span class="python_keyword">lambda</span> x: x.author.name == user and x.created >= time.today(),
			issue_worklogs)</code></pre>