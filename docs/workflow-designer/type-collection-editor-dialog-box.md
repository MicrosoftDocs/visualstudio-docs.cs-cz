---
title: Návrhář postupu provádění – dialogové okno Editor kolekcí typů
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 023d049c5256abe6212dd65df78cd67151be94a2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593054"
---
# <a name="type-collection-editor-dialog-box"></a>Dialogové okno Editor typu kolekce

Dialogové okno **Editor kolekcí typů** slouží k přidání známých typů do aktivit **odeslání** a **příjem** . Toto dialogové okno se používá také k přidání argumentů obecného typu do aktivity **InvokeMethod** . V případě, že se používá pro aktivity **odeslání** a **přijetí** pro přidání známých typů, dialogové okno **Editor kolekce typů** vyžaduje, aby doplňky typu byly jedinečné. Pokud je přidán duplicitní typ a změna je potvrzena kliknutím na tlačítko **OK**, je vrácena chybová zpráva. Při použití pro aktivitu **InvokeMethod** k přidání argumentů obecného typu umožňuje dialogové okno **Editor kolekce typů** přidat duplicitní typy.

Další informace najdete v tématu [známé typy kontraktu dat](/dotnet/framework/wcf/feature-details/data-contract-known-types).

Následující tabulka popisuje prvky uživatelského rozhraní (UI) v dialogovém okně **kolekce typů** .

|Prvek uživatelského rozhraní (UI)|Popis|
|-|-----------------|
|**Seznam typů**|Seznam typů, které byly přidány nebo odebrány.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Chcete-li zobrazit Editor kolekce typů pro aktivity odeslat a přijmout

1. V zobrazení Návrh vyberte aktivitu **Odeslat** nebo **přijmout** .

2. Stisknutím klávesy **F4** otevřete okno **vlastnosti** .

3. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami vedle vlastnosti **KnownTypes** .

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Chcete-li vyvolat Editor kolekce typů pro aktivitu InvokeMethod

1. V zobrazení Návrh vyberte aktivitu **InvokeMethod** .

2. Stisknutím klávesy **F4** otevřete okno **vlastnosti** .

3. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami vedle vlastnosti **genericTypeArguments** .
