来源Hugh [和光同尘hugh](javascript:void(0);)

**影响版本**

![image-20230817150348901](./泛微9存在sql注入.assets/image-20230817150348901.png)

```
(1)/E-mobile/flowdo_page.php?diff=delete&RUN_ID=1  //参数RUN_ID
(2)/E-mobile/flowdo_page.php?diff=delete&flowid=1  //参数flowid
(3)/E-mobile/flowsorce_page.php?flowid=2
(4)/E-mobile/flownext_page.php?diff=candeal&detailid=2
(5)/E-mobile/flowimage_page.php?FLOW_ID=2
(6)/E-mobile/flowform_page.php?FLOW_ID=2
(7)/E-mobile/diaryother_page.php?searchword=23
(8)/E-mobile/create/ajax_do.php?diff=word&sortid=1       //参数sortid
(9)/E-mobile/create/ajax_do.php?diff=word&idstr=2       //参数idstr
(10)/E-mobile/flow/freeflowimg.php?RUN_ID=1             
(11)/E-mobile/create/ajax_do.php?diff=addr&sortid=1     //参数sortid
(12)/E-mobile/create/ajax_do.php?diff=addr&userdept=1  //参数userdept
(13)/E-mobile/create/ajax_do.php?diff=addr&userpriv=1 //参数userpriv
(14)/E-mobile/create/ajax_do.php?diff=wordsearch&idstr=1  //参数idstr
(15)/E-mobile/flow/flowhave_page.php?detailid=2,3
(16)/E-mobile/flow/flowtype_free.php?flowid=1
(17)/E-mobile/flow/flowtype_free.php?runid=1
(18)/E-mobile/flow/flowtype_other.php?flowid=1
(19)/E-mobile/flow/flowtype_other.php?runid=1
(20)/E-mobile/flow/freeflowimage_page.php?fromid=2
(21)/E-mobile/flow/freeflowimage_page.php?diff=new&runid=2  //参数runid

```



