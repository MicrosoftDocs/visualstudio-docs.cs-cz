---
title: XML schémata
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d01c56b04a9b046f695a19d61a9b47fcac73e06
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592331"
---
# <a name="xml-schemas-dialog-box"></a>Dialogové okno Schémata XML

Dialogové okno **schémata XML** slouží k výběru schémat XML Schema Definition Language (XSD), která mají být přidružena k dokumentu XML. Můžete vybrat schéma z mezipaměti schématu nebo zadat schéma, které se nenachází v mezipaměti. Vybraná schémata se považují za součást sady schémat. Sada schémat se používá pro technologii IntelliSense a také pro ověřování dokumentů XML.

Můžete otevřít dialogové okno **schémata XML** kliknutím na tlačítko **schémata** v okně Vlastnosti dokumentu, nebo výběrem **schémat** z nabídky **XML** .

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

**Použití**

Vyberte způsob použití schématu XML.

- **Automatický:** Toto schéma není používáno aktuálním dokumentem, ale je k dispozici pro automatické přidružení. Pokud dokument XML deklaruje obor názvů, který odpovídá `targetNamespace` tohoto schématu, schéma bude automaticky přidruženo a je zahrnuto do sady schémat.

- **Použijte toto schéma**. Toto schéma je používáno aktuálním dokumentem. Uživatel explicitně požadoval, aby se toto schéma používalo kliknutím na tento sloupec, nebo jestli se schéma automaticky přidružil na základě odpovídajícího `targetNamespace`.

- **Nepoužívejte Vybraná schémata**. Toto schéma není používáno aktuálním dokumentem, a to ani v případě, že má schéma shodnou `targetNamespace`. Toto nastavení může být užitečné při řešení konfliktů, pokud existuje více než jedna verze stejného schématu v mezipaměti schématu nebo řešení.

**Cílový obor názvů**

Zobrazí cílový obor názvů přidružený ke schématu XML.

**Název souboru**

Zobrazí název souboru schématu XML.

**Add**

Otevře dialogové okno **otevřít schéma XSD** , které umožňuje vybrat další schémata, která se mají přidat do sady schémat. Když do sady schémat přidáte schéma, hodnota **použít** sloupec je nastavená na **použít toto schéma**.

**odebrat**

Odebere aktuálně vybrané schéma ze sady schémat. Tím se odebere schéma z mezipaměti schématu v paměti, ale ne ze systému souborů.

## <a name="see-also"></a>Viz také:

- [Postupy: Výběr schémat XML k použití](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Mezipaměť schématu](../xml-tools/schema-cache.md)
