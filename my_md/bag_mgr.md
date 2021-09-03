#关于对客户端bag_mgr代码的学习
##函数

>**def vardump(o)**
>>1.暂时还不知道有什么用，可能是以前的代码，现在还未有用处

>**def build_ham_com_info( ham )**
>>1.并没有被调用到，猜测是用来输出线上信息

>**def PlayerSprite_MergeFrom_UserPresent(o, m)**
>>1.用来判断玩家账号是否存在，判断其性别，id，头像
>>2.使用**HasField()**来判断某个key是否存在

>**def UserInfo_MergeFrom_UserPresent(o, m)**
>>1.作用和上一个函数相类似，但是判断的信息更多

>**def UserDetailedInfo_MergeFrom_UserPresent(o, m)**
>>1.调用了上一个函数，主要是用来给用户增加一些tag，上一个函数信息并不完整

###class item_ex
>**def \_\_init\_\_(self)**
>>1.暂时还不知道有什么用，可能是以前的代码，现在还未有用处

###class cBagMgr(cMgrBase)
>**def \_\_init\_\_(self)**
>>1.初始化装备，商品，商店信息

>**def init(self)**
>>1.注册消息响应
>>2.调用了**globals.py**中的**def listen(f)**，
>>3.使用了util库中的listen函数,函数中使用了**registor_respond**，用于给**fix_laoshu.py**传入数据


>**def ForgeItemResult(self, m)**
>>1.使用了**cache_mgr.py**里定义的**def fire_notify(self, cmd, argv)**函数，触发通知，打印日志
>>```
>>self.fire_notify( "Forge_Item_Result", m )
>>```
>>```
>>    # 触发通知
>>    def fire_notify(self, cmd, argv):
>>        try:
>>            log3("fire_notify: %s %s", cmd, argv)
>>            if sys.is_small_client:
>>                process_fired_noity(cmd, argv)
>>            if self._cmd_cb != None:
>>                self._cmd_cb(cmd, argv)
>>        except:
>>            msg = traceback.format_exc()
>>            log(msg)
>>```

>**def InviteVisit(self, m)**
>>1.使用了**cache_mgr.py**里定义的**def fire_notify(self, cmd, argv)**函数，触发通知，打印日志
>>```
>>self.fire_notify( "Invite_Visit", m )
>>```

>**def init_shop(self, db_mgr )**
>>1.初始化商店的table

>**def reset(self)**
>>1.提供一个重置的方法,在重新登录的时候，需要重置
>>2.重置了item

>**def clear(self)**
>>1.调用了**fix_laoshu.py**中的**un_registor_respond_by_catalog( "bag" )**
>>2.还不太清楚**un_registor_respond_by_catalog**函数意义，但估计是清除某些不需要的数据
>>```
>>    def un_registor_respond_by_catalog( catalog ):
>>        id_list = []
>>        for id in cNetPacketRespondMgr._catalog_mag :
>>            if cNetPacketRespondMgr._catalog_mag[ id ] == catalog :
>>                id_list.append( id )
>>                
>>        for id in id_list :
>>            del cNetPacketRespondMgr._id_map[id]
>>            del cNetPacketRespondMgr._catalog_mag[id]
>>        pass
>>    un_registor_respond_by_catalog = staticmethod( un_registor_respond_by_catalog )  
>>```

>**def test_cmd_cb(self, cmd, argv )**
>>1.用于测试内部指令

>**def add_item(self, m )**
>>1.添加一个物品

>**def get_item( self, id )**
>>1.返回物品的id

>**def get_item_by_name(self, name)**
>>1.根据物品的名字得到一个id

>**def get_item_by_item_type_sn(self, item_type_sn)**
>>1.扫描物品类型，如果类型相同，则返回该物品

>**def remove_item(self, id )**
>>1.删除一个物品

>**def get_bag_item_list(self, ids, counts, names )**
>>1.得到背包内物品的信息,如id,数量，名称

>**def get_bag_item_id_list(self, ids, test_func = None, compare_fc = None )**
>>1.得到背包内物品的id

>**def get_shop_item_list(self, names, prices)**
>>1.得到商店内物品的信息,id,数量

>**def get_item_price(self, name )**
>>1.返回商品价格

>**def onItem(self, m)**
>>1.判断商品是否在表内
>>2.在本地数据文件中不存在的物品，就不进行添加，同时加以log
>>3.对需要添加的物品，调用**add_item**函数

>**def onItemDisappear(self, m)**
>>1.调用**remove_item**函数删除物品

>**def set_cmd_cb(self, cb)**
>>1.调用了**cache_mgr.py**里的**set_cmd_cb(self, cb)**函数设置回调函数，回调指令cb
>>```
>>    cMgrBase.set_cmd_cb(self, cb)
>>    errord.set_cmd_cb(cb)
>>```
>>```
>># 设置回调
>>    def set_cmd_cb(self, cb):
>>        self._cmd_cb = c
>>```

>**def DialogHospital(self, m)**
>>1.调用**HasField**函数，判断是否存在key，并打印日志

>**def PackItem(self, m)**
>>1.仅仅只是打印日志

>**def notify_junk_shop(self, cache)**
>>1.声明并更新当铺列表

>**def notify_confirm_sell_junk(self, m, v)**
>>1.得到物品卖出的价格

>**def notify_bag_changed(self)**
>>1.声明背包的变化

>**def notify_stall(self, user_sn, stall)**
>>1.该含税并未被调用过，怀疑跟宠物系统有关

###class cBagMgrHelper

