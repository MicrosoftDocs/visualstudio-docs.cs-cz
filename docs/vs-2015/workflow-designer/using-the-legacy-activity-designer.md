---
title: Používání starší verze návrháře aktivit | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: a6c8aafe9eac26080bfbf57d06c7d512d1e1e62d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843428"
---
# <a name="using-the-legacy-activity-designer"></a>Používání starší verze návrháře aktivit
Toto téma popisuje způsob použití návrháře aktivit v starší [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Použít starší verzi návrháře při cílení [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Návrhář aktivity umožňuje vytvářet vlastní vlastní aktivity.  
  
## <a name="creating-a-custom-activity"></a>Vytvoření vlastní aktivity  
 Postupujte podle těchto kroků můžete vytvořit vlastní aktivitu pomocí návrháře aktivit:  
  
1. Na **projektu** nabídky, klikněte na tlačítko **přidat aktivitu**.  
  
2. Vyberte **aktivity** nebo **aktivita (s rozdělením kódu)** šablony.  
  
   1.  Použití **aktivity** šablony k vytvoření aktivity se definici aktivity a kódem uživatele ve stejném souboru kódu.  
  
   2.  Použití **aktivita (s rozdělením kódu)** šablony k vytvoření aktivity s aktivity definicí vyjádřenou jako značka pracovního postupu a kód uživatele v samostatném souboru kódu.  
  
3. Zadejte název aktivity nebo Ponecháme výchozí název a potom klikněte na tlačítko **přidat**.  
  
   Sadu vlastních aktivit můžete vytvořit také tak, že vytvoříte nový projekt typu **knihovny aktivit pracovních postupů**. Další informace o tomto typu projektu naleznete v tématu [postupy: vytvoření knihovny aktivit pracovních postupů (starší verze)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).  
  
## <a name="configuring-an-activity"></a>Konfigurace aktivity  
 Návrhář aktivity je aktivní, můžete použít prohlížeč vlastností ke konfiguraci vlastností uvedených v následující tabulce.  
  
|Vlastnost|Komentáře|  
|--------------|--------------|  
|**Jméno**|Název aktivity.|  
|**Základní třída**|Základní třída, která je odvozena z aktivity. Výchozí základní třída je [aktivitu typu SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020). V **vlastnosti** okna, klikněte na tlačítko **základní třída** symbol tří teček **[...]**  k výběru jiné základní třídy v [Procházet a vybrat typ dialogovému oknu rozhraní .NET (starší verze)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|  
|**Popis**|Uživatelsky definovaný popis aktivity.|  
|**Povoleno**|Nastavte na **True** ve výchozím nastavení k povolení spuštění aktivit a ověřování. Nastavte na **False** zakázat provádění aktivity a ověřování. Informace o spuštění aktivit a ověřování najdete v tématu [vývoj aktivit pracovního postupu](http://go.microsoft.com/fwlink?LinkID=65024).|  
  
## <a name="adding-child-activities"></a>Přidání podřízených aktivit  
 Podřízené aktivity můžete přetáhnout z panelu nástrojů na aktivitu, která při návrhu. Potom můžete nakonfigurovat každou podřízenou aktivitu pomocí prohlížeče vlastností.  
  
## <a name="see-also"></a>Viz také  
 [Vývoj aktivit pracovního postupu](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Vytváření vlastních aktivit](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Aktivity starších verzí pracovních postupů](../workflow-designer/legacy-workflow-activities.md)   
 [Ukázky vlastních aktivit](http://go.microsoft.com/fwlink?LinkID=65022)   
 [Postupy: vytvoření knihovny aktivit pracovních postupů (starší verze)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md)   
 [Používání starší verze návrháře postupu provádění](../workflow-designer/using-the-legacy-workflow-designer.md)