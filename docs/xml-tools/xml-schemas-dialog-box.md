---
title: XML schémata
description: Seznamte se s dialog schémat XML, který slouží k výběru schémat XML schématu definice jazyka (XSD), která mají být přidružena k dokumentu XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1c91e97d0508ab85893409386ddd3ab9dded7f45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874831"
---
# <a name="xml-schemas-dialog-box"></a>Dialogové okno Schémata XML

Dialogové okno **schémata XML** slouží k výběru schémat XML Schema Definition Language (XSD), která mají být přidružena k dokumentu XML. Můžete vybrat schéma z mezipaměti schématu nebo zadat schéma, které se nenachází v mezipaměti. Vybraná schémata se považují za součást sady schémat. Sada schémat se používá pro technologii IntelliSense a také pro ověřování dokumentů XML.

Můžete otevřít dialogové okno **schémata XML** kliknutím na tlačítko **schémata** v okně Vlastnosti dokumentu, nebo výběrem **schémat** z nabídky **XML** .

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

**Použití**

Vyberte způsob použití schématu XML.

- **Automatický:** Toto schéma není používáno aktuálním dokumentem, ale je k dispozici pro automatické přidružení. Pokud dokument XML deklaruje obor názvů, který odpovídá `targetNamespace` tomuto schématu, schéma bude automaticky přidruženo a je zahrnuto do sady schémat.

- **Použijte toto schéma**. Toto schéma je používáno aktuálním dokumentem. Uživatel explicitně požadoval, aby se toto schéma používalo kliknutím na tento sloupec, nebo jestli se schéma automaticky přidružil na základě odpovídajícího typu `targetNamespace` .

- **Nepoužívejte Vybraná schémata**. Toto schéma není používáno aktuálním dokumentem, a to ani v případě, že má schéma shodu `targetNamespace` . Toto nastavení může být užitečné při řešení konfliktů, pokud existuje více než jedna verze stejného schématu v mezipaměti schématu nebo řešení.

**Cílový obor názvů**

Zobrazí cílový obor názvů přidružený ke schématu XML.

**Název souboru**

Zobrazí název souboru schématu XML.

**Přidat**

Otevře dialogové okno **otevřít schéma XSD** , které umožňuje vybrat další schémata, která se mají přidat do sady schémat. Když do sady schémat přidáte schéma, hodnota **použít** sloupec je nastavená na **použít toto schéma**.

**Odebrat**

Odebere aktuálně vybrané schéma ze sady schémat. Tím se odebere schéma z mezipaměti schématu v paměti, ale ne ze systému souborů.

## <a name="see-also"></a>Viz také

- [Postupy: Výběr schémat XML k použití](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Mezipaměť schémat](../xml-tools/schema-cache.md)
