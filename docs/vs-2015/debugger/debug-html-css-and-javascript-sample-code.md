---
title: Ladění ukázkový kód HTML, CSS a JavaScript | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 51893967-98c8-4141-ba40-03646f221760
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c4793747e85435b63361df03cdb011d38b214e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51720783"
---
# <a name="debug-html-css-and-javascript-sample-code"></a>Ladění ukázkový kód HTML, CSS a JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Kód v tomto tématu se ukázkový soubor pro [rychlý start: ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md). Chyby podle návrhu k dispozici v tomto rychlém startu jsou opravené v této verzi kódu.  
  
## <a name="sample-code"></a>Ukázkový kód  
 Následující kód HTML je používán \<text > značky v tomto rychlém startu.  
  
```html  
<div id="flipTemplate" data-win-control="WinJS.Binding.Template"  
         style="display:none">  
    <div class="fixedItem" >  
        <img src="#" data-win-bind="src: flipImg" />  
    </div>  
</div>  
<div id="fView" data-win-control="WinJS.UI.FlipView" data-win-options="{  
    itemDataSource: Data.items.dataSource, itemTemplate: flipTemplate }">  
</div>  
```  
  
 Následující šablony stylů CSS ukazuje přidání provedené default.css.  
  
```css  
#fView {  
    background-color:#0094ff;  
    height: 500px;  
    margin: 25px;  
}  
```  
  
 Následující příklad kódu ukazuje kompletní kód jazyka JavaScript v souboru default.js. Odkazy na obory názvů WinJS pro tento kód se v souboru default.html šablony.  
  
```javascript  
(function () {  
    "use strict";  
  
    var app = WinJS.Application;  
    var activation = Windows.ApplicationModel.Activation;  
  
    var myData = [];  
    for (var x = 0; x < 4; x++) {  
        myData[x] = { flipImg: "/images/logo.png" }  
    };  
  
    var pages = new WinJS.Binding.List(myData, { proxy: true });  
  
    app.onactivated = function (args) {  
        if (args.detail.kind === activation.ActivationKind.launch) {  
            if (args.detail.previousExecutionState !==  
            activation.ApplicationExecutionState.terminated) {  
                // TODO: . . .  
            } else {  
                // TODO: . . .  
            }  
            args.setPromise(WinJS.UI.processAll());  
  
            updateImages();  
        }  
    };  
  
    function updateImages() {  
  
        pages.setAt(0, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223195" });  
        pages.setAt(1, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223196" });  
        pages.setAt(2, { flipImg: "http://go.microsoft.com/fwlink/?LinkID=223197" });  
    };  
  
    app.oncheckpoint = function (args) {  
    };  
  
    app.start();  
  
    var publicMembers = {  
        items: pages  
    };  
  
    WinJS.Namespace.define("Data", publicMembers);  
  
})();  
```  
  
## <a name="see-also"></a>Viz také  
 [Rychlý start: Ladění kódu HTML a CSS](../debugger/quickstart-debug-html-and-css.md)



