---
UID: NF:wudfwdm.InsertTailList
title: InsertTailList function
author: windows-driver-content
description: The InsertTailList routine inserts an entry at the tail of a doubly linked list of LIST_ENTRY structures.
old-location: kernel\inserttaillist.htm
old-project: kernel
ms.assetid: 9eb470c8-ee37-497e-982e-d32b4b9b7348
ms.author: windowsdriverdev
ms.date: 3/1/2018
ms.keywords: InsertTailList, InsertTailList routine [Kernel-Mode Driver Architecture], k109_8f31d6a6-89a0-440c-9397-2bef61a5878f.xml, kernel.inserttaillist, wdm/InsertTailList
ms.prod: windows-hardware
ms.technology: windows-devices
ms.topic: function
req.header: wudfwdm.h
req.include-header: Wdm.h, Ntddk.h, Ntifs.h, Wudfwdm.h
req.target-type: Desktop
req.target-min-winverclnt: Available starting with Windows 2000.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Any level (see Remarks section)
topic_type:
-	APIRef
-	kbSyntax
api_type:
-	HeaderDef
api_location:
-	Wdm.h
api_name:
-	InsertTailList
product: Windows
targetos: Windows
req.typenames: PO_FX_PERF_STATE_UNIT, *PPO_FX_PERF_STATE_UNIT
req.product: Windows 10 or later.
---

# InsertTailList function


## -description


The <b>InsertTailList</b> routine inserts an entry at the tail of a doubly linked list of <a href="https://msdn.microsoft.com/library/windows/hardware/ff554296">LIST_ENTRY</a> structures.


## -syntax


````
VOID InsertTailList(
  _Inout_ PLIST_ENTRY ListHead,
  _Inout_ PLIST_ENTRY Entry
);
````


## -parameters




### -param ListHead [in, out]

Pointer to the <a href="https://msdn.microsoft.com/library/windows/hardware/ff554296">LIST_ENTRY</a> structure that represents the head of the list.


### -param Entry [in, out]

Pointer to a <a href="https://msdn.microsoft.com/library/windows/hardware/ff554296">LIST_ENTRY</a> structure that represents the entry to be inserted in the list.


## -returns



None




## -remarks



<b>InsertTailList</b> updates <i>ListHead</i>-&gt;<b>Blink</b> to point to <i>Entry</i>. It updates <i>Entry</i>-&gt;<b>Blink</b> to point to the old last entry in the list, and sets <i>Entry</i>-&gt;<b>Flink</b> to <i>ListHead</i>. The <b>Flink</b> of the previous last entry is updated to point to <i>Entry</i> as well.

For information about using this routine when implementing a doubly linked list, see <a href="https://msdn.microsoft.com/library/windows/hardware/ff563802">Singly and Doubly Linked Lists</a>.

Callers of <b>InsertTailList</b> can be running at any IRQL. If <b>InsertTailList</b> is called at IRQL &gt;= DISPATCH_LEVEL, the storage for <i>ListHead</i> and the list entries must be resident.




## -see-also

<a href="..\wudfwdm\nf-wudfwdm-islistempty.md">IsListEmpty</a>



<a href="..\wudfwdm\nf-wudfwdm-insertheadlist.md">InsertHeadList</a>



<a href="..\wudfwdm\nf-wudfwdm-initializelisthead.md">InitializeListHead</a>



<a href="..\wudfwdm\nf-wudfwdm-removetaillist.md">RemoveTailList</a>



<a href="..\wudfwdm\nf-wudfwdm-removeheadlist.md">RemoveHeadList</a>



<a href="..\wdm\nf-wdm-exinterlockedinserttaillist.md">ExInterlockedInsertTailList</a>



 

 

