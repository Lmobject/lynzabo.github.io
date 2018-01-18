---
approvers:
- brendandburns
- davidopp
title: 故障排除
---

在使用Kubernetes遇到错误时候，可以查找这个文档快速解决问题。我们从两部分介绍怎么排除故障:

   * [排除应用故障](/docs/tasks/debug-application-cluster/debug-application/) - 排除Kubernetes上部署的应用故障。
 
   * [排除集群故障](/docs/tasks/debug-application-cluster/debug-cluster/) - 方便集群管理员排查集群问题。

你也可以从[release](https://github.com/kubernetes/kubernetes/releases)获取你想要的答案。

## 获得帮助

如果你的问题通过上面几种方式都没有获得解决办法，你可以通过各种方式寻求Kubernetes团队获得帮助。

### Questions

The documentation on this site has been structured to provide answers to a wide
range of questions. [Concepts](/docs/concepts/) explain the Kubernetes
architecture and how each component works, while [Setup](/docs/setup/) provides
practical instructions for getting started. [Tasks](/docs/tasks/) show how to
accomplish commonly used tasks, and [Tutorials](/docs/tutorials/) are more
comprehensive walkthroughs of real-world, industry-specific, or end-to-end
development scenarios. The [Reference](/docs/reference/) section provides
detailed documentation on the [Kubernetes API](/docs/api-reference/{{page.version}}/)
and command-line interfaces (CLIs), such as [`kubectl`](/docs/user-guide/kubectl-overview/).

You may also find the Stack Overflow topics relevant:

   * [Kubernetes](http://stackoverflow.com/questions/tagged/kubernetes)
   * [Google Kubernetes Engine](http://stackoverflow.com/questions/tagged/google-container-engine)

## Help! My question isn't covered!  I need help now!

### Stack Overflow

Someone else from the community may have already asked a similar question or may
be able to help with your problem. The Kubernetes team will also monitor
[posts tagged Kubernetes](http://stackoverflow.com/questions/tagged/kubernetes).
If there aren't any existing questions that help, please [ask a new one](http://stackoverflow.com/questions/ask?tags=kubernetes)!

### Slack

The Kubernetes team hangs out on Slack in the `#kubernetes-users` channel. You
can participate in discussion with the Kubernetes team [here](https://kubernetes.slack.com).
Slack requires registration, but the Kubernetes team is open invitation to
anyone to register [here](http://slack.kubernetes.io). Feel free to come and ask
any and all questions.

Once registered, browse the growing list of channels for various subjects of
interest. For example, people new to Kubernetes may also want to join the
`#kubernetes-novice` channel. As another example, developers should join the
`#kubernetes-dev` channel.

There are also many country specific/local language channels. Feel free to join
these channels for localized support and info:

- France: `#fr-users`, `#fr-events`
- Germany: `#de-users`, `#de-events`
- Japan: `#jp-users`, `#jp-events`

### Mailing List

The Kubernetes / Google Kubernetes Engine mailing list is [kubernetes-users@googlegroups.com](https://groups.google.com/forum/#!forum/kubernetes-users)

### Bugs and Feature requests

If you have what looks like a bug, or you would like to make a feature request,
please use the [Github issue tracking system](https://github.com/kubernetes/kubernetes/issues).

Before you file an issue, please search existing issues to see if your issue is
already covered.

If filing a bug, please include detailed information about how to reproduce the
problem, such as:

* Kubernetes version: `kubectl version`
* Cloud provider, OS distro, network configuration, and Docker version
* Steps to reproduce the problem