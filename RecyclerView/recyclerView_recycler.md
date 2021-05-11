# RecyclerView 源码阅读

RecyclerView 重要组成部分

- **Recycler**
- **Adapter**
- **LayoutManager**
- **ViewHolder**

## Recycler

> ```java
> /**
>  * A Recycler is responsible for managing scrapped or detached item views for reuse.
>  *
>  * <p>A "scrapped" view is a view that is still attached to its parent RecyclerView but
>  * that has been marked for removal or reuse.</p>
>  *
>  * <p>Typical use of a Recycler by a {@link LayoutManager} will be to obtain views for
>  * an adapter's data set representing the data at a given position or item ID.
>  * If the view to be reused is considered "dirty" the adapter will be asked to rebind it.
>  * If not, the view can be quickly reused by the LayoutManager with no further work.
>  * Clean views that have not {@link android.view.View#isLayoutRequested() requested layout}
>  * may be repositioned by a LayoutManager without remeasurement.</p>
>  */
> ```

通过Recycler的描述文字可以看出它的主要职责是管理scraped和detached item

`scrapped` 表示这个视图还是依附在RecyclerView，但是被标记成已去除或者重用

通过LayoutManager获取adapter数据集的视图，该视图表示给定位置或项目ID上的数据，如果要重用的视图被认为是“脏的”，则将要求adapter重新绑定它。如果不是则layoutmanager可以快速重用该视图，无需进行进一步工作。被认为是干净的视图无需调用request layout，可以由layout Manager重新定位，无需重新测量。

