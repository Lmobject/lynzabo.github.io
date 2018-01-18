---
layout: docwithnav
title: 贡献Kubernetes文档
---

<!-- BEGIN: Gotta keep this section JS/HTML because it swaps out content dynamically -->
<p>&nbsp;</p>
<script language="JavaScript">
var forwarding=window.location.hash.replace("#","");
$( document ).ready(function() {
    if(forwarding) {
        $("#generalInstructions").hide();
        $("#continueEdit").show();
        $("#continueEditButton").text("Edit " + forwarding);
        $("#continueEditButton").attr("href", "https://github.com/kubernetes/website/edit/{{ page.docsbranch }}/" + forwarding)
        $("#viewOnGithubButton").text("View " + forwarding + " on GitHub");
        $("#viewOnGithubButton").attr("href", "https://git.k8s.io/website/" + forwarding)
    } else {
        $("#generalInstructions").show();
        $("#continueEdit").hide();
    }
});
</script>
<div id="continueEdit">

<h2>Continue your edit</h2>

<p><b>To make changes to the document, do the following:</b></p>

<ol>
<li>Click the button below to edit the page you were just on.</li>
<li>Click <b>Commit Changes</b> at the bottom of the screen to create a copy of our site in your GitHub account called a <i>fork</i>.</li>
<li>You can make other changes in your fork after it is created, if you want.</li>
<li>On the index page, click <b>New Pull Request</b> to let us know about it.</li>
</ol>

<p><a id="continueEditButton" class="button"></a></p>
<p><a id="viewOnGithubButton" class="button"></a></p>

</div>
<div id="generalInstructions">

<h2>编辑网站</h2>

<p>点击下方的按钮到我们网站的repo。你可以点击<b>Fork</b>按钮去拷贝一份代码到你的Github账户上。在你的仓库上做修改，修改完后，你可以提交一个<b>New Pull Request</b>给我们，发送你的修改请求。</p>

<p><a class="button" href="https://github.com/kubernetes/website/">浏览网站源码</a></p>

</div>
<!-- END: Dynamic section -->

<br/>

想了解更多如何贡献Kubernetes文档，可以看：

* [创建一个文档Pull Request](/docs/home/contribute/create-pull-request/)
* [写一个新的主题](/docs/home/contribute/write-new-topic/)
* [如何在本地运行Kubernetes文档](/docs/home/contribute/stage-documentation-changes/)
* [使用Page Templates](/docs/home/contribute/page-templates/)
* [编写文档风格指导](/docs/home/contribute/style-guide/)
