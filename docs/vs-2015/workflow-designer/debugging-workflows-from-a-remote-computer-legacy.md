---
title: Ladění pracovních postupů ze vzdáleného počítače (starší verze) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 2b3627b6d62b1f4d237c2f2013d332be56b58fc6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191580"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Ladění pracovních postupů ze vzdáleného počítače (starší verze)
Toto téma popisuje, jak ladit vzdálenou starší verze [!INCLUDE[wf](../includes/wf-md.md)] aplikace, které jsou vytvořeny tak, starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Použijte starší [!INCLUDE[wfd2](../includes/wfd2-md.md)] když vaše aplikace potřebuje cílit na platformu [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Při instalaci [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)], jednu z možností součásti instalace je instalace [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] ladicího programu pro [!INCLUDE[wf](../includes/wf-md.md)]. Tím se nainstaluje komponenty vzdáleného ladění. Tyto komponenty vzdáleného ladění musí být nainstalován v počítači, který cílíte pro pracovní postup vzdáleného ladění.  
  
 Sestavení obsahující definice pracovního postupu starší verzi pracovního postupu, který právě ladíte ve vzdáleném počítači musí být navíc nainstalována v globální mezipaměti sestavení (GAC), který právě ladíte z místního počítače. Například pokud starší verzi pracovního postupu běží ve vzdáleném počítači A a ladí z místního počítače B, definice pracovního postupu musí být k dispozici v GAC počítači B. To umožňuje návrháře k deserializaci a zobrazení v počítači B značka pracovního postupu pracovního postupu, který běží vzdáleně na počítači A. Další informace o globální mezipaměti sestavení naleznete v knihovně MSDN.  
  
 [!INCLUDE[wf2](../includes/wf2-md.md)] vzdálené ladění funguje stejně jako vzdálené ladění pro ostatní [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] komponenty. Další informace najdete v tématu [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] vzdálené ladění v knihovně MSDN.  
  
## <a name="see-also"></a>Viz také  
 [Ladění starších verzí pracovních postupů](../workflow-designer/debugging-legacy-workflows.md)