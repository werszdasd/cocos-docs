
# 姿态暂存

姿态图中无法将一个姿态结点的输出连接至多个结点，当你试图连接姿态结点至新的结点时，旧的连接将被断开。若需要在多处复用一个姿态，需要用到姿态暂存。

## 概念

**姿态暂存** 是指将一张姿态图的结果存储起来，并在其它姿态图中使用该图产生的姿态的机制。**姿态暂存对象**（下称姿态暂存或暂存）是实现这样机制的手段，它关联了一张姿态图。

> 一个形象但不完全的理解是将姿态暂存视为保存了姿态对象的缓存变量。

姿态暂存归属于动画图层级。每个层级都可以创建多项暂存，创建后，可以在该层级中的任何姿态图中通过 **使用暂存姿态** 结点来引用该暂存。

姿态暂存允许被引用多次，其所关联的姿态图每帧仅会被更新、求值一次。

## 编辑姿态暂存

在选定动画图层级的属性检查器上可以查看、创建、编辑该层级的所有姿态暂存：

![Alt text](layer-stashes.png)

点击 [编辑] 按钮开始编辑选定暂存所关联的姿态图。

## 使用暂存的姿态

在任意姿态图中，创建结点的菜单里列举了所有可以使用的暂存。点选后将创建 **使用暂存姿态** 结点。

![Alt text](use-stash-node-list.png)

![Alt text](use-stash-node.png)

**使用暂存姿态** 结点输出指定暂存所产生的姿态；该结点没有额外输入。

双击 **使用暂存姿态** 结点，可进入该结点所关联的暂存的编辑界面。

## 快捷方式：暂存此图

很多时候并不是设计之初就能想到要暂存哪些姿态；更多的情况是在已经开发了一张图知乎，才发现需要将这张图复用在多处。
为此，可在任意姿态图中单击右键进入上下文菜单，并单击执行菜单项 [暂存此图]：

![Alt text](menu-item-stash-this-pose.png)

执行后，当前图中原本的内容将被移动到一项新建的姿态暂存中，并且会在当前图中生成一个 **使用暂存姿态** 结点来引用新建的姿态暂存。