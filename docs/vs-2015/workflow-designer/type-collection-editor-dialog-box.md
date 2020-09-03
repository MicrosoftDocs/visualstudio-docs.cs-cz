---
title: Dialogové okno Editor kolekcí typů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dae99166b8b811df75f2e2777d176e6778b60c7d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670151"
---
# <a name="type-collection-editor-dialog-box"></a>Dialogové okno Editor typu kolekce
Dialogové okno **Editor kolekcí typů** slouží k přidání známých typů do aktivit **odeslání** a **příjem** . Toto dialogové okno se používá také k přidání argumentů obecného typu do aktivity **InvokeMethod** . V případě, že se používá pro aktivity **odeslání** a **přijetí** pro přidání známých typů, dialogové okno **Editor kolekce typů** vyžaduje, aby doplňky typu byly jedinečné. Pokud je přidán duplicitní typ a změna je potvrzena kliknutím na tlačítko **OK**, je vrácena chybová zpráva. Při použití pro aktivitu **InvokeMethod** k přidání argumentů obecného typu umožňuje dialogové okno **Editor kolekce typů** přidat duplicitní typy.

> [!NOTE]
> [!INCLUDE[crabout](../includes/crabout-md.md)] známé typy, viz [známé typy kontraktu dat](https://msdn.microsoft.com/library/1a0baea1-27b7-470d-9136-5bbad86c4337).

 Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **kolekce typů** .

|Prvek uživatelského rozhraní (UI)|Popis|
|----------------|-----------------|
|**Seznam typů**|Seznam typů, které byly přidány nebo odebrány.|

## <a name="to-bring-up-the-type-collection-editor"></a>Chcete-li vyvolat Editor kolekce typů

#### <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Chcete-li zobrazit Editor kolekce typů pro aktivity odeslat a přijmout

1. V zobrazení Návrh vyberte aktivitu **Odeslat** nebo **přijmout** .

2. Stisknutím klávesy **F4** otevřete okno **vlastnosti** .

3. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami vedle vlastnosti **KnownTypes** .

#### <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Chcete-li vyvolat Editor kolekce typů pro aktivitu InvokeMethod

1. V zobrazení Návrh vyberte aktivitu **InvokeMethod** .

2. Stisknutím klávesy **F4** otevřete okno **vlastnosti** .

3. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami vedle vlastnosti **genericTypeArguments** .