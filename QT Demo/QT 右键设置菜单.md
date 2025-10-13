```cpp
// 设置上下文菜单策略为自定义

ui->tableView->setContextMenuPolicy(Qt::CustomContextMenu);

// 连接自定义上下文菜单请求信号到槽函数
    connect(ui->tableView, SIGNAL(customContextMenuRequested(QPoint)), this, SLOT(showContexMenu(QPoint)));
    

void testCustomTable::showContexMenu(const QPoint &pos)

{
    // 创建菜单
    QMenu menu(this);

    QAction *actionDelete = menu.addAction("删除");

    // 连接菜单动作的触发信号到槽函数
    connect(actionDelete, SIGNAL(triggered(bool)), this, SLOT(slotDeletSelectPatient()));

    // 在鼠标位置显示菜单
    menu.exec(ui->tableView->viewport()->mapToGlobal(pos));

}
```