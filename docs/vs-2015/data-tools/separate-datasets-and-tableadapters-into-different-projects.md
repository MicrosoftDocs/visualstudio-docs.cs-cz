---
title: Oddělení datových sad a TableAdapters do různých projektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, separating Datasets and TableAdapters
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e94c76254b14bdf82e4e7a219cbb0f35cb532f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824319"
---
# <a name="separate-datasets-and-tableadapters-into-different-projects"></a>Rozdělování datových sad a objektů TableAdapter do různých projektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Vylepšili jsme typové datové sady, aby [objekty TableAdapter](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) a do samostatné projekty se můžou generovat třídy datové sady. To umožňuje rychle samostatné aplikace a generovat vícevrstvých datových aplikací.  
  
 Následující postup popisuje proces používání[vytváření a úpravy typované datové sady](../data-tools/creating-and-editing-typed-datasets.md) pro generování kódu datovou sadu do projektu, který je oddělen od projektu, který obsahuje vygenerovanou `TableAdapter` kódu.  
  
## <a name="separatedatasets-and-tableadapters"></a>Separatedatasets a objektů TableAdapters  
 Když oddělíte datové sady kód z `TableAdapter` kód projektu, který obsahuje kód datové sady se musí nacházet v aktuálním řešení. Pokud není tento projekt v aktuálním řešení, nebude k dispozici v **projektu DataSet** v seznamu **vlastnosti** okna.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-separate-the-dataset-into-a-different-project"></a>Chcete rozdělit datovou sadu do jiného projektu  
  
1. Otevřete řešení, které obsahuje sadu dat (soubor XSD).  
  
   > [!NOTE]
   >  Pokud řešení obsahuje projekt, do kterého chcete rozdělení kódu datovou sadu, vytvořte projekt nebo přidat existující projekt do řešení.  
  
2. Poklikejte na soubor (soubor XSD) typové datové sady v **Průzkumníka řešení** otevření datové sady v **Návrhář Dataset**.  
  
3. Vyberte prázdnou oblast **Návrhář Dataset**.  
  
4. V **vlastnosti** okna, vyhledejte **projektu DataSet** uzlu.  
  
5. V **projektu DataSet** vyberte název projektu, do které chcete generovat kód datové sady.  
  
    Jakmile vyberete projekt, do které chcete generovat kód datovou sadu **soubor datové sady** vlastnost se vyplní výchozí název souboru. Tento název lze změnit v případě potřeby. Kromě toho pokud chcete generovat kód datovou sadu do konkrétního adresáře, můžete nastavit **složky projektu** nastavte na název složky.  
  
   > [!NOTE]
   >  Když oddělíte datové sady a objekty TableAdapter (nastavením **projektu DataSet** vlastnost), existující částečné třídy v projektu nebudou automaticky přesunuty. Existující částečné třídy datové sady je nutné ručně přesunout do projektu datové sady.  
  
6. Uložte datovou sadu.  
  
    Generování kódu datovou sadu do vybraného projektu v **projektu DataSet** vlastnost a **TableAdapter** do aktuálního projektu bude vygenerován kód.  
  
   Ve výchozím nastavení po oddělíte datové sady a `TableAdapter` kód, výsledek je soubor samostatné třídy v každém projektu. Původní projekt obsahuje soubor s názvem DatasetName.Designer.vb (nebo DatasetName.Designer.cs), který obsahuje `TableAdapter` kódu. Projekt, který je zadaný ve **projektu Dataset** vlastnost obsahuje soubor s názvem DatasetName.DataSet.Designer.vb (nebo DatasetName.DataSet.Designer.cs), která obsahuje kód datové sady.  
  
> [!NOTE]
>  Chcete-li zobrazit soubor generované třídy, vyberte datovou sadu nebo `TableAdapter` projektu. Potom v **Průzkumníka řešení**vyberte **zobrazit všechny soubory** .  
  
## <a name="see-also"></a>Viz také  
 [Přehled vícevrstvých datových aplikací](../data-tools/n-tier-data-applications-overview.md)   
 [Návod: Vytvoření vícevrstvé datové aplikace](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Hierarchická aktualizace](../data-tools/hierarchical-update.md)   
 [Přístup k datům v sadě Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](http://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca)

