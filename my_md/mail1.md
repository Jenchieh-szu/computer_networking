#关于邮件系统mail1.py的学习
###class wnd_mail(cWndBase)
>**1. def __init__(self)**
>>1.初始化邮件list和邮件

>**2. def init_module_write_mail(self)**
>>1. 调用邮件书写模块
>>2. 执行**set_cmd_cb**

>**3. def init_module_receive_mail(self)**
>>1. 调用邮件接收模块

>**4. def init_wnd(self)**
>>1. 初始化显示窗口
>>2. 调用模块：click模块，按钮点击模块，鼠标进出按钮模块
>>3. 初始化按钮样式

>**5. def clear(self)**
>>1. 清空窗口，dlc，邮件

>**6. def init_dlc_maillist(self)**
>>1. 初始化dlc的邮件list

>**7. def init_ani_num(self)**
>>1. 初始化黄金和钻石的数量

>**8. def bag_changed(self)**
>>1. 获取玩家的黄金，钻石数量

>**9. def set_gold_num(self,num)**
>>1. 设定游戏窗口黄金的数量

>**10. def set_diamond_num(self,num)**
>>1. 设定游戏窗口钻石的数量

>**11. def mail_has_next_page(self)**
>>1. 判断四种类型的邮件页数是否大于1

>**11. def query_mail_list(self,config = 'remain')**
>>1. 调用了**cache_mgr.py**中的**register_page_view**函数进行注册
>>2. 通过该函数判断邮件列表界面的打开、翻页，打开邮件界面需要用**register_page_view**函数进行注册
>>3. 关闭邮件界面还需要调用**cache_mgr.py**中的**unregister_page_view**函数进行注销

>**11. def wnd_show(self)**
>>1. 显示邮件界面，调用初始化

>**12. def get_tl_info(self,kind) 和 def get_tl_detail(self,kind)** 
>>1. 两函数代码几乎一样，返回函数不相同，**def get_tl_detail**没有被引用
>>2. 用来返回id等信息

>**13. def get_size_by_tl_kind(self,kind=None)**
>>1. 得到信息的大小

>**14. def wnd_hide(self)**
>>1. 将所有列表清空，将窗口也清空

>**15. def on_scroll_changed(self,name,pos)**
>>1. 应该是书写输入变化

>**16. def on_notify_cb( self, cmd, argv )**
>>1. 暂不清楚用处

>**17. def on_drag_btn_down_cb( self, name )**
>>1. 应该跟按钮按下有关，按钮名字被替换了，替换后被传入dlc和邮件书写模块

>**18. def on_drag_btn_up_cb( self, name )**
>>1. 应该跟按钮弹起有关，按钮名字被替换了，替换后被传入dlc和邮件书写模块

>**19. def on_btn_clicked(self,cmd,argv)**
>>1. 鼠标点击事件的cmd
>>2. 不同的按钮不同的事件

>**20. def highlight_tag_text(self,pos)**
>>1. 高亮tag

>**21. def darken_tag_text(self,pos)**
>>1. 熄灭tag

>**22. def darken_all_tag_text(self)**
>>1. 熄灭所有tag

>**23. def on_button_enter_cb(self,name)**
>>1. 鼠标进入按钮时，高亮tag

>**24. def on_button_exit_cb(self,name)**
>>1. 鼠标离开按钮时，熄灭tag

>**25. def on_update_pos_cb_mail(self,game_wnd, item, child_postfix)**
>>1. 应该是邮件打开操作

>**24. def sort_func(self,sn)**
>>1. 得到邮件的生成时间

>**25. def mails(self,all_mails)**
>>1. 得到邮件的所有信息

>**26. def refresh_sys_present(self)**
>>1. 刷新系统

>**27. def filter_system_mail(self,all_mails)**
>>1. 过滤系统邮件

>**28. def filter_sent_mail(self,all_mails)**
>>1. 过滤已发送邮件

>**29. def filter_friend_mail(self,all_mails)**
>>1. 过滤好友邮件

>**30. def refresh_readpoint(self)**
>>1. 刷新未读小红点

>**31. def init_readpoint(self)**
>>1. 初始化未读小红点

>**32. def set_mail_list(self,_type)**
>>1. 设定当前过滤的类型

>**33. def get_post_mask_and_list(self,post_sn)**
>>1. 应该是查看邮件是否已读，并且激活黑幕

>**34. def refresh_mail_list(self)**
>>1. 刷新邮件列表

>**35. def delete_mail(self，post_sn)**
>>1. 调用**cache_mgr.py**的**batch_destroy_posts**对邮件进行删除

>**36. def delete_all(self)**
>>1. 删除某个类型的全部邮件，除了 未领取物品的邮件 和 未读邮件 还有 已读但未领取物品的邮件

>**37. def delete_all_read(self)**
>>1. 删除全部邮件

>**38. def delete_friend_read(self)**
>>1. 删除好友邮件

>**39. def delete_all_sent(self)**
>>1. 删除已发送的邮件

>**40. def delete_system_read(self)**
>>1. 删除系统的邮件

>**41. def pickup_all(self)**
>>1. 一键领取所有物品

>**42. def update(self,deta)**
>>1. 刷新邮件，黄金，钻石

>**43. def execute(self,cmd,argv)**
>>1. 执行模块，如删除邮件，点击回复后，进入邮件的书写并自动添加收件人

###class mail_module_write
>**1. def __init__(self,wnd)**
>>1. 初始化邮件书写模块

>**2. def clear(self)**
>>1. 清空模块

>**3. def set_cmd_cb(self,cmd_cb)**
>>1. 设定当前的指令cb

>**4. def fire_cmd(self,cmd,argv)**
>>1. 调用指令

>**5. def init_dlc_friendlist(self)**
>>1. 初始化好友名单

>**6. def on_scroll_changed(self,name,pos)**
>>1. 应该是书写输入变化

>**7. def on_notify_cb(self, cmd, argv)**
>>1. 通知模块？

>**8. def on_drag_btn_down_cb(self,name)**
>>1. 右侧滑块下拉

>**9. def on_drag_btn_up_cb(self,name)**
>>1. 右侧滑块上拉

>**10. def on_input_focus_cb(self,name,flag)**
>>1. 对输入的内容，好友名字，主题，内容进行显示

>**11. def on_input_keydown_cb(self,name,key)**
>>1. 设定输入的格式

>**12. def active(self)**
>>1. 激活邮件书写框

>**13. def deactive(self)**
>>1. 关闭邮件书写框

>**14. def open_friend_list(self)**
>>1. 打开好友列表

>**15. def close_friend_list(self)**
>>1. 关闭好友列表

>**16.  def on_update_pos_cb_friend(self,game_wnd, item, child_postfix)**
>>1. 刷新好友列表和信息

>**17. def change_friend_key(self)**
>>1. 查找好友，且替换其中的空格

>**18. def execute(self,cmd,argv)**
>>1. 执行cmd操作，可以打开或关闭好友列表，还有发送邮件

>**19. def set_receiver_name(self,usn)**
>>1. 设定收件人名字

>**20. def update(self,deta)**
>>1. 刷新邮件书写系统

>**21. def prepare_face(face_sn)**
>>1. 得到头像

###class mail_module_receive
>**1. def __init__(self,wnd)**
>>1. 初始化接收邮件界面

>**2. def set_cmd_cb(self,cmd_cb)**
>>1. 设定当前的指令cb

>**3. def fire_cmd(self,cmd,argv)**
>>1. 调用指令

>**4. def deactive(self)**
>>1. 激活pn_mask,背后的黑幕

>**5. def set_info(self)**
>>1. 设定是否已接收到邮件

>**6. def on_scroll_changed(self)**
>>1. 显示邮件接收内容

>**7. def set_post_sn(self,post_sn)**
>>1. 设置回复信息

>**8. def set_btn_reply(self)**
>>1. 设置回复按钮

>**9. set_sender_name(self,sender_name)**
>>1. 设置发送方名字

>**10. set_subject(self,subject)**
>>1. 设置发送邮件背景和主题

>**11. set_body(self,body)**
>>1. 设置邮件的主题文字

>**12. def set_date(self,date)**
>>1. 设置回收发件时间

>**13. mail_with_present(self,post_sn)**
>>1. 显示有礼物的邮件内容界面

>**12. def mail_without_present(self,post_sn)**
>>1. 显示没有礼物的邮件内容界面

>**12. def execute(self,cmd,argv)**
>>1. 执行cmd指令





