---
title: Řešení potíží s programu Help Viewer | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting [Help Viewer 2.0]
- Help Viewer 2.0, troubleshooting
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a3497d46ed4c9c5a04d8f40cc3056ea282593884
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934233"
---
# <a name="troubleshooting-the-help-viewer"></a>Řešení potíží s programem Help Viewer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma popisuje problémy, které se můžete setkat s aplikací Help Viewer.  
  
## <a name="audio-doesnt-work"></a>Zvuk nefunguje.  
 Aplikace Help Viewer neobsahuje zvukový přehrávač. Pokud si stáhnete obsah, který obsahuje audio a nic se nestane při výběru **Přehrát**, nainstalujte si zvukový přehrávač.  
  
## <a name="search-doesnt-work-in-windows-server-2008-windows-server-2008-with-sp1-or-windows-server-2008-r2"></a>Hledání nefunguje ve Windows serveru 2008, Windows Server 2008 s aktualizací SP1 nebo Windows Server 2008 R2.  
 Funkce vyhledávání a filtrování v aplikaci Help Viewer vyžadují instalaci služby Windows Search a na. Ve výchozím nastavení tato služba je vypnuto ve Windows serveru 2008, Windows Server 2008 s aktualizací Service Pack 1 (SP1) a Windows Server 2008 R2.  
  
#### <a name="to-activate-windows-search-service"></a>Aktivace služby Windows Search  
  
1.  Spusťte správce serveru.  
  
2.  V levém navigačním podokně zvolte **role**.  
  
3.  V podokně Souhrn rolí zvolte **přidat roli**.  
  
4.  Vyberte roli Souborová služba a klikněte na tlačítko **Další** tlačítko.  
  
5.  Zvolte službu role Windows Search.  
  
## <a name="additional-resources"></a>Další prostředky  
 Můžete získat další informace a poskytování zpětné vazby v aplikaci Help Viewer pomocí následující prostředky:  
  
- Chcete-li poskytnout zpětnou vazbu, přečtěte si téma [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) na Microsoft webu nebo odešlete e-mail na [ hlpfdbk@microsoft.com ](mailto:hlpfdbk@microsoft.com).  
  
- Další informace najdete v tématu [dokumentaci pro vývojáře a systém nápovědy](http://go.microsoft.com/fwlink/?LinkId=232741) fóra a [The Help Guy](http://go.microsoft.com/fwlink/?LinkId=232743) blogu.  
  
## <a name="see-also"></a>Viz také  
 [Příručka Help Viewer 2.1 Správce](http://go.microsoft.com/fwlink/?LinkId=243985)



