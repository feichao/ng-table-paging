# table-paging 使用文档

标签（空格分隔）： table-paging

[Github][1]

---

### table-paging 是一个方便为 table 添加分页功能的组件。

#### 1.目前支持三种分页组件样式
 - load\_more 模式：在 table 的底部渲染出两个按钮，“加载更多”和“加载全部”；
 - load\_pre\_next模式：在 table 的底部渲染出两个按钮，“上一页”和“下一页”；
 - load\_paging模式：使用 wan-material-paging 组件渲染出带具体页码的分页组件。

---

#### 2. 主要有一下两种使用方式
 - 后台一次返回所有数据，但是返回数据比较多，前端想要提高页面渲染速度；
 - 后台分页返回数据。

---

#### 3. 使用说明
 - 针对第一种使用方式，即后台返回所有数据，可以使用任意组件样式；
 - 针对第二种使用方式，即后台分页返回数据，分为两种情况：
     - 如果后台返回了所有数据的条数，则可以使用任意组件样式；
     - 如果后台没有返回所有数据条数，则只能使用 load\_more 和 load\_pre\_next 模式。 

---

#### 4. 组件 scope 说明
 - tpModel（=）：table 组件的数据集；
 - tpPagingModel（=）：table 组件的分页数据集，在 table tr repeat 时使用 tpPagingModel 代替 tpModel；
 - tpType（@）：指定分页样式，默认为 load_more；
 - tpTotal（=）：指定所有数据的条数；
 - tpPagesize（@）：指定每页显示的数据条数，默认为 20；
 - tpAsync（&）：指定从后台获取数据的方法，会传入一个 currentPage 参数。**如果没有指定 tpAsync，则默认后台返回了所有数据，tpTotal 会自动取 tpModel 的 length。**
 
---

#### 5. Demo

 - 如果后台返回所有数据，此时 tp_type 可以取任意样式值。
```
<table-paging tp-model="vm.users" tp-paging-model="vm.filterUsers" tp-type="load_more">
   <table>
        <thead>
            <tr>
                <th>name</th>
                <th>email</th>
            </tr>
        </thead>
        <tbody>
            <!-- 此处要使用 vm.filterUsers -->
            <tr ng-repeat="user in vm.filterUsers">
                <td>{{user.name}}</td>
                <td>{{user.email}}</td>
            </tr>
        </tbody>
    </table>
</table-paging>
```

 - 如果后台后台分页返回数据，而且返回了具体的条数。可以使用任意组件样式。
```
<table-paging tp-model="vm.users" tp-paging-model="vm.filterUsers" tp-total="vm.userTotal" tp-type="load_more">
   <table>
        <thead>
            <tr>
                <th>name</th>
                <th>email</th>
            </tr>
        </thead>
        <tbody>
            <!-- 此处要使用 vm.filterUsers -->
            <tr ng-repeat="user in vm.filterUsers">
                <td>{{user.name}}</td>
                <td>{{user.email}}</td>
            </tr>
        </tbody>
    </table>
</table-paging>
```

 - 如果后台后台分页返回数据，但是没有返回具体的条数。
```
<table-paging tp-model="vm.users" tp-paging-model="vm.filterUsers" tp-type="load_more">
   <table>
        <thead>
            <tr>
                <th>name</th>
                <th>email</th>
            </tr>
        </thead>
        <tbody>
            <!-- 此处要使用 vm.filterUsers -->
            <tr ng-repeat="user in vm.filterUsers">
                <td>{{user.name}}</td>
                <td>{{user.email}}</td>
            </tr>
        </tbody>
    </table>
</table-paging>
```

<iframe style="width: 100%; height: 1000px;" src="http://o8tapqn1p.bkt.clouddn.com/20170619-table-paging.demo.html"></iframe>


    [1]: https://github.com/feichao/ng-table-paging


