---
title: 'Postupy: vytvoření konzolových aplikací sekvenčních pracovních postupů (starší verze) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: e467e4a574263eaa35640bc99f99c1f599a74df9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306316"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Postupy: vytvoření konzolových aplikací sekvenčních pracovních postupů (starší verze)
Postupujte podle těchto kroků a vytvořte projekt konzolové aplikace sekvenčního pracovního postupu pomocí starší verze [!INCLUDE[wfd1](../includes/wfd1-md.md)] poskytované [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Použijte starší [!INCLUDE[wfd2](../includes/wfd2-md.md)] potřeba cílit na platformu [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>K vytvoření konzolové aplikace sekvenčního pracovního postupu  
  
1.  Spusťte sadu Visual Studio.  
  
2.  Na **souboru** nabídky, přejděte k **nový**a pak vyberte **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
3.  Vyberte buď **rozhraní .NET Framework 3.0** možnost nebo **rozhraní .NET Framework 3.5** možnost v rozevíracím seznamu v horní části **nový projekt** okna pro přístup k starší verze návrháře.  
  
    > [!NOTE]
    >  Výchozí možnost v [!INCLUDE[vs2010](../includes/vs2010-md.md)] je **rozhraní .NET Framework 4**. Tato možnost slouží k vytvoření [!INCLUDE[wf](../includes/wf-md.md)] aplikací, které se zaměřují [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] a nepoužívá starší verze návrháře.  
  
4.  V **typy projektů** podokně vyberte projekty Visual C# nebo projekty jazyka Visual Basic (v části **jiné jazyky**) a pak vyberte **pracovního postupu**.  
  
5.  V **šablony** vyberte **Konzolová aplikace sekvenčního pracovního postupu**.  
  
6.  V **název** zadejte popisný název pro váš projekt, aby byl snadno identifikovat.  
  
7.  V **umístění** zadejte adresář, ve kterém chcete projekt uložit, nebo klikněte na tlačítko **Procházet** přejít k němu.  
  
     Návrhář formulářů Windows se otevře a zobrazí Form1 projektu, který jste vytvořili.  
  
8.  Klikněte na tlačítko **OK**.  
  
     Návrháře postupu provádění otevře a zobrazí návrhovou plochu pracovní postup sekvenčního pracovního postupu, který jste vytvořili.  
  
9. Přetáhněte aktivitu z **nástrojů** na návrhovou plochu v **přetáhněte aktivitu** určené oblasti.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření projektů pracovních postupů starších verzí](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Vývoj pracovních postupů](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)