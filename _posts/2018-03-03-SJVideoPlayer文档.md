---
title:  "SJVideoPlayer 文档"
---
陆续更新中...

# 播放一个视频
### SJVideoPlayerURLAsset
此类用于初始化视频资源. 由Media的URL及一些附加信息创建.

示例:
```Objective-C
videoPlayer.URLAsset =
[[SJVideoPlayerURLAsset alloc] initWithAssetURL:assetURL
                                     scrollView:tableView
                                      indexPath:indexPathOfCell
                                   superviewTag:playerParentView.tag];
```
如果你想播放一个视频资源, 并将播放器添加到一个普通视图或Cell中, 需要使用此类的初始化方法创建一个模型并赋值给播放器. 例如在某个 TableViewCell 中播放视频:

### 初始化接口:

1 - 在普通视图上播放:

```Objective-C

- (instancetype)initWithAssetURL:(NSURL *)assetURL;

- (instancetype)initWithAssetURL:(NSURL *)assetURL
                       beginTime:(NSTimeInterval)beginTime;
```
* 如果你的视频是在一个普通的视图上播放, 可以使用上面两个方法去初始化.
- beginTime   此为视频开始播放的时间, 当不为 0 时, 视频将会跳转到指定的时间进行播放. 单位是秒.


2 - 在 Cell 中播放

```Objective-C

- (instancetype)initWithAssetURL:(NSURL *)assetURL
                      scrollView:(__unsafe_unretained UIScrollView * __nullable)tableOrCollectionView
                       indexPath:(NSIndexPath * __nullable)indexPath
                    superviewTag:(NSInteger)superviewTag;

- (instancetype)initWithAssetURL:(NSURL *)assetURL
                       beginTime:(NSTimeInterval)beginTime
                      scrollView:(__unsafe_unretained UIScrollView *__nullable)tableOrCollectionView
                       indexPath:(NSIndexPath *__nullable)indexPath
                    superviewTag:(NSInteger)superviewTag;
```
* 如果 tableView 作为主要视图, 视频在 cell 中播放, 可以使用这两个方法初始化.
- beginTime   视频开始播放的时间, 当不为 0 时, 视频将会跳转到指定的时间进行播放. 单位是秒.
- scrollView   此为 table view 或者 collection view
- indexPath   此为播放器 cell 所在的位置.
- superviewTag   此为播放器父视图的 tag. 播放器将要滚动出现时, 需要使用此 tag 找到父视图.

3 - 在 Table Header View 上播放

```Objective-C

- (instancetype)initWithAssetURL:(NSURL *)assetURL
                       beginTime:(NSTimeInterval)beginTime
    playerSuperViewOfTableHeader:(__weak UIView *)superView
                       tableView:(UITableView *)tableView;

- (instancetype)initWithAssetURL:(NSURL *)assetURL
                       beginTime:(NSTimeInterval)beginTime
     collectionViewOfTableHeader:(__weak UICollectionView *)collectionView
         collectionCellIndexPath:(NSIndexPath *)indexPath
              playerSuperViewTag:(NSInteger)playerSuperViewTag
                   rootTableView:(UITableView *)rootTableView;
```
* 如果 tableView 作为主要视图, 视频在 Table header view 中播放, 可以使用这两个方法初始化.
* 此部分第二个方法主要考虑 header view 中存在 collection view 的情况. 例如某个商品页, header view 是商品视频和图片介绍组成, 这样的情况一般都是使用 collection view 去实现的.
- beginTime   此为视频开始播放的时间, 当不为 0 时, 视频将会跳转到指定的时间进行播放. 单位是秒.
- playerSuperViewOfTableHeader   此为播放器的父视图.
- collectionViewOfTableHeader    此为header view 中的 collection view.
- collectionCellIndexPath   此为播放器 cell 在 collection view 中的位置.
- playerSuperViewTag   此为播放器父视图的 tag. 播放器将要滚动出现时, 需要使用此 tag 找到父视图.

4 - 嵌套的情况
* video player -> collection cell -> collection view -> table cell -> table view

```Objective-C
- (instancetype)initWithAssetURL:(NSURL *)assetURL
                       beginTime:(NSTimeInterval)beginTime // unit is sec.
                       indexPath:(NSIndexPath *__nullable)indexPath
                    superviewTag:(NSInteger)superviewTag
             scrollViewIndexPath:(NSIndexPath *__nullable)scrollViewIndexPath
                   scrollViewTag:(NSInteger)scrollViewTag
                  rootScrollView:(__unsafe_unretained UIScrollView *__nullable)rootScrollView;

```
* 如果 tableView 作为主要视图, 视频在 collection cell 中播放, 而 collection view 却在 table view 中, 这种情况可以使用此方法初始化.
- beginTime   此为视频开始播放的时间, 当不为 0 时, 视频将会跳转到指定的时间进行播放. 单位是秒.
- indexPath   此为播放器 cell 所在的位置.
- superviewTag   此为播放器父视图的 tag. 播放器将会依据此 tag 作为条件之一, 来判断是否滚动出现.
- scrollViewIndexPath   此为 collection view 所在的 table cell 位于 table view 中的位置.
- scrollViewTag   此为 collection view 的 tag. 播放器将会依据此 tag 作为条件之一, 来判断是否滚动出现.
