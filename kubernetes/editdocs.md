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
        $("#continueEditButton").attr("href", "https://github.com/Lynzabo/lynzabo.github.io/edit/{{ page.docsbranch }}" + "/kubernetes/" + forwarding)
        $("#viewOnGithubButton").text("View " + forwarding + " on GitHub");
        $("#viewOnGithubButton").attr("href", "https://github.com/Lynzabo/lynzabo.github.io/blob/{{ page.docsbranch }}/kubernetes/" + forwarding)
    } else {
        $("#generalInstructions").show();
        $("#continueEdit").hide();
    }
});
</script>
<div id="continueEdit">

<h2>继续编辑</h2>

<p><b>如果要编辑这个文件,请按照下面进行操作:</b></p>

<ol>
<li>点击下面的编辑按钮进入Github上当前页面地址</li>
<li>点击<b>Fork this repository and propose changes</b>按钮,Fork一份网站源码代码,并自动打开这个页面的编辑界面.</li>
<li>填写修改后的文件内容,点击<b>Propose file change</b>按钮提交修改,并进入请求合并界面.</li>
<li>然后点击<b>Create pull request</b>发送一个合并请求,等待管理员同意合并.</li>
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
