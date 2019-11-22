---
title: Používání starší verze návrháře aktivit | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a13aeeb3394ee6b8896376c0e7d520b90fb56fa6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302820"
---
# <a name="using-the-legacy-activity-designer"></a>Používání starší verze návrháře aktivit
Toto téma popisuje, jak používat návrháře aktivit ve starších [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Použijte starší verzi návrháře, pokud cílíte na [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] nebo [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Návrhář aktivity umožňuje vytvářet vlastní aktivity.

## <a name="creating-a-custom-activity"></a>Vytvoření vlastní aktivity
 Pomocí následujících kroků můžete vytvořit vlastní aktivitu pomocí návrháře aktivit:

1. V nabídce **projekt** klikněte na příkaz **Přidat aktivitu**.

2. Vyberte šablonu **aktivita** nebo aktivita **(s rozdělením kódu)** .

   1. Pomocí šablony **aktivity** můžete vytvořit aktivitu s definicí aktivity a kódem uživatele ve stejném souboru kódu.

   2. Použijte šablonu **aktivita (s rozdělením kódu)** k vytvoření aktivity s definicí aktivity vyjádřenou jako značky pracovního postupu a kódem uživatele v samostatném souboru kódu.

3. Zadejte název aktivity nebo ponechte výchozí název a potom klikněte na **Přidat**.

   Můžete také vytvořit sadu vlastních aktivit vytvořením nového projektu typu **Knihovna aktivit pracovního postupu**. Další informace o tomto typu projektu naleznete v tématu [How to: Create a Workflow Activity Library (starší verze)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>Konfigurace aktivity
 I když je Návrhář aktivity aktivní, můžete použít prohlížeč vlastností ke konfiguraci vlastností uvedených v následující tabulce.

|Vlastnost|Komentáře|
|--------------|--------------|
|**Název**|Název aktivity|
|**Základní třída**|Základní třída, ze které je odvozena aktivita. Výchozí základní třída je [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). V okně **vlastnosti** klikněte na tři tečky **základní třídy** **[...]** pro výběr jiné základní třídy v [dialogovém okně Procházet a vyberte možnost typ .NET (starší verze)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**Popis**|Uživatelsky definovaný Popis aktivity.|
|**Umožněn**|Ve výchozím nastavení nastavte na **hodnotu true** , aby se povolilo provádění a ověřování aktivity. Nastavte na **hodnotu false** , chcete-li zakázat provádění a ověřování aktivity. Informace o provádění a ověřování aktivit najdete v tématu [vývoj aktivit pracovních postupů](https://go.microsoft.com/fwlink?LinkID=65024).|

## <a name="adding-child-activities"></a>Přidávání podřízených aktivit
 Podřízené aktivity lze přetáhnout ze sady nástrojů na aktivitu, kterou navrhujete. Potom můžete nakonfigurovat každou podřízenou aktivitu pomocí prohlížeče vlastností.

## <a name="see-also"></a>Viz také
 [Vývoj aktivit pracovních postupů](https://go.microsoft.com/fwlink?LinkID=65024) , které [vytvářejí vlastní aktivity](https://go.microsoft.com/fwlink?LinkID=65021) [starší aktivity pracovních postupů](../workflow-designer/legacy-workflow-activities.md) [](https://go.microsoft.com/fwlink?LinkID=65022) [, popisují postupy: Vytvoření knihovny aktivity pracovního postupu (starší verze)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md) [pomocí starší verze Návrhář postupu provádění](../workflow-designer/using-the-legacy-workflow-designer.md)