
一：基本模型

1、UI中添加一个QListView
2、源文件中 声明一个 QStringListModel * mModel;
3、设置数据

```cpp
       QStringList data;
       data<<"1"<<"2"<<"3";
      mModel->setStringListData();
      ```

4、View设置Model
    // 设置模型
```cpp
    ui->listView->setModel(mModel);
```
5、编辑模型
```cpp
     QStringList dataTemp = mModel->stringList()
     dataTemp << "666";
     // 重新设置Model后视图会自动更新
    mModel->setStringList(dataTemp);
```


二：表格模型

1、创建model
```cpp
     QStandardItemModel *mModel = new QStandardItemModel(3,0,this);
```
2、设置表头
```cpp
     mModel->setHorizontalheaderLables({"姓名"});
```
3、设置子Item
```cpp
     mModel->setItem(0,0,new QStandardItem("张三"));
     mModel->setItem(1,0,new QStandardItem("李四");
     mModel->setItem(2,0,new QStandardItem("李四");
```
4、设置Model
```cpp
      ui->tableView->setModel(mModel);
```
      
三：自定义表格模型

1、创建model
```cpp

```