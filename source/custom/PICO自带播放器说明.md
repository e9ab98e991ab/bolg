    title: PICO自带播放器说明
    date: 2018-04-15 11:22:02
---

1.         通过广播控制播放器的暂停/继续播放
  com.picovr.wing.player.playorpause
  发送这条广播，如果播放器当前是播放状态，则暂停；暂停状态，则继续播放。
2.         通过广播控制播放器的退出
  com.picovr.wing.player.exit发送这条广播，播放过程会中断，应用退出。
3.         通过广播获取播放器当前状态
  com.picovr.wing.player.status

