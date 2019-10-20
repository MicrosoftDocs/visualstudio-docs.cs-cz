---
title: 'Návrhář postupu provádění: Přidání nové položky do projektu pracovního postupu'
ms.date: 06/25/2018
ms.topic: conceptual
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a87efc24ef148600c31dbb07d7517f9235306102
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650418"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Postupy: Přidání nové položky do projektu pracovního postupu

Po vytvoření projektu pracovního postupu můžete do projektu přidat aktivity pracovního postupu, návrháře a další známé položky aplikace Visual Studio.

V následující tabulce jsou uvedeny položky programovací model Windows Workflow Foundation (WF), které můžete přidat do projektu pracovního postupu:

| Name | Popis |
|-| - |
| Aktivita | Aktivita, která se skládá z jiných činností. Výběrem této položky se do projektu přidá stejný soubor XAML, který byste získali při výběru šablony **knihovny aktivit** pro nový projekt. Další informace o tomto postupu najdete v tématu [Vytvoření projektu pracovního postupu](creating-a-workflow-project.md). |
| Návrhář aktivit | Návrhář pro přizpůsobení prostředí aktivity v době návrhu. Výběr této položky přidá do projektu stejné soubory, jako byste získali při výběru šablony **knihovny návrháře aktivit** pro nový projekt. |
| Aktivita kódu | Aktivita s logikou provádění zapsanou v kódu. Soubor zdrojového kódu s přepsáním metody <xref:System.Activities.CodeActivity.Execute%2A> je již pro vás vygenerován. |
| Služba pracovního postupu WCF | Služba [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] sestavená pomocí aktivit pracovního postupu. Výběr této položky přidá stejné soubory do projektu, jak byste získali při výběru šablony **aplikace služby pracovního postupu WCF** pro nový projekt. Další informace o tomto postupu najdete v tématu [Postup: Vytvoření aplikace služby pracovního postupu WCF](/visualstudio/workflow-designer/creating-a-workflow-project). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Přidání nové položky do projektu pracovního postupu

1. V nabídce **projekt** vyberte možnost **Přidat novou položku**.

   Otevře se dialogové okno **Přidat novou položku** .

1. V levém podokně vyberte kategorii **pracovního postupu** a potom vyberte šablonu položky pracovního postupu.

   > [!NOTE]
   > Pokud nevidíte kategorii **pracovního postupu** , nainstalujte nejprve součást **programovací model Windows Workflow Foundation** sady Visual Studio. Podrobné pokyny najdete v tématu [instalace programovací model Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. Do pole **název** v dolní části dialogového okna zadejte název položky.

1. Vyberte **Přidat** a přidejte položku do projektu.

## <a name="see-also"></a>Viz také:

- [Vytvořit projekt pracovního postupu](../workflow-designer/creating-a-workflow-project.md)