thread-source-study

# 一、对象内存布局

​		在 Hotspot 虚拟机中，对象在内存中的存储布局，可以分 为三个区域:对象头(Header)、实例数据(Instance Data)、对 齐填充(Padding)。

​		![对象内存布局](./对象内存布局.png)

​		对象头记录了对象和锁有关的信息，当某个对象被 synchronized 关键字当成同步锁时，那么围绕这个锁的一 系列操作都和 Mark word 有关系。 

<table width="384.30" border="0" cellpadding="0" cellspacing="0" style='width:384.30pt;border-collapse:collapse;table-layout:fixed;'>
   <col width="151.20" span="2" class="xl65" style='mso-width-source:userset;mso-width-alt:2184;'/>
   <col width="197.45" class="xl65" style='mso-width-source:userset;mso-width-alt:4157;'/>
   <col width="169.95" class="xl65" style='mso-width-source:userset;mso-width-alt:2984;'/>
   <col width="163.30" class="xl65" style='mso-width-source:userset;mso-width-alt:2700;'/>
   <col width="151.20" span="16379" class="xl65" style='mso-width-source:userset;mso-width-alt:2184;'/>
   <tr height="19.10" style='height:19.10pt;mso-height-source:userset;mso-height-alt:382;'>
    <td class="xl66" height="36.70" width="51.20" rowspan="2" style='height:36.70pt;width:51.20pt;border-right:1.0pt solid #EEEEEE;border-bottom:1.5pt solid #DDDDDD;' x:str>锁状态</td>
    <td class="xl67" width="148.65" colspan="2" style='width:148.65pt;border-right:1.0pt solid #EEEEEE;border-bottom:1.5pt solid #DDDDDD;' x:str>25bit</td>
    <td class="xl67" width="69.95" rowspan="2" style='width:69.95pt;border-right:1.0pt solid #EEEEEE;border-bottom:1.5pt solid #DDDDDD;' x:str>4bit</td>
    <td class="xl67" width="63.30" style='width:63.30pt;' x:str>1bit</td>
    <td class="xl82" width="51.20" style='width:51.20pt;' x:str>2bit</td>
   </tr>
   <tr height="17.60" style='height:17.60pt;'>
    <td class="xl70" x:str>23bit</td>
    <td class="xl70" x:str>2bit</td>
    <td class="xl83" x:str>是否偏向锁</td>
    <td class="xl84" x:str>锁标志位</td>
   </tr>
   <tr height="17.60" style='height:17.60pt;'>
    <td class="xl72" height="17.60" style='height:17.60pt;' x:str>无锁</td>
    <td class="xl73" colspan="2" style='border-right:none;border-bottom:none;' x:str>对象的hashCode</td>
    <td class="xl75" x:str>对象分代年龄</td>
    <td class="xl85" x:num>0</td>
    <td class="xl86" x:num>1</td>
   </tr>
   <tr height="17.60" style='height:17.60pt;'>
    <td class="xl76" height="17.60" style='height:17.60pt;' x:str>偏向锁</td>
    <td class="xl77" x:str>线程ID</td>
    <td class="xl77" x:str>Epoch</td>
    <td class="xl77" x:str>对象分代年龄</td>
    <td class="xl81" x:num>1</td>
    <td class="xl87" x:num>1</td>
   </tr>
   <tr height="20.60" style='height:20.60pt;mso-height-source:userset;mso-height-alt:412;'>
    <td class="xl78" height="20.60" style='height:20.60pt;' x:str>轻量级锁</td>
    <td class="xl79" colspan="4" style='border-right:1.0pt solid #EEEEEE;border-bottom:1.0pt solid #DDDDDD;' x:str>指向栈中锁记录的指针</td>
    <td class="xl88" x:num>0</td>
   </tr>
   <tr height="19.10" style='height:19.10pt;mso-height-source:userset;mso-height-alt:382;'>
    <td class="xl76" height="19.10" style='height:19.10pt;' x:str>重量级锁</td>
    <td class="xl77" colspan="4" style='border-right:1.0pt solid #EEEEEE;border-bottom:1.0pt solid #DDDDDD;' x:str>指向互斥量(重量级锁)的指针</td>
    <td class="xl87" x:num>10</td>
   </tr>
   <tr height="19.10" style='height:19.10pt;mso-height-source:userset;mso-height-alt:382;'>
    <td class="xl78" height="19.10" style='height:19.10pt;' x:str>GC标记</td>
    <td class="xl79" colspan="4" style='border-right:1.0pt solid #EEEEEE;border-bottom:1.0pt solid #DDDDDD;' x:str>空</td>
    <td class="xl88" x:num>11</td>
   </tr>
  </table>

