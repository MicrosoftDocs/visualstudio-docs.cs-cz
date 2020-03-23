---
title: Speciální znaky k útěku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1b17ded468e262d4f636ed5494081adab7b8c5f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632248"
---
# <a name="special-characters-to-escape"></a>Speciální znaky k útěku

Speciální znaky musí být uvozeny pouze v případě, že mají zvláštní význam v kontextu, ve kterém jsou používány. Například hvězdička (*) je speciální znak pouze v atributech "Zahrnout" a "Vyloučit" definice položky nebo ve volání <xref:Microsoft.Build.Tasks.CreateItem>. Ve všech ostatních případech je hvězdička považována za doslovnou hvězdičku. I když nemusíte uniknout hvězdičky všude v souborech projektu, tím není na škodu.

 Místo speciálního\<znaku použijte notaci % \<xx>, kde xx> představuje šestnáctkovou hodnotu znaku ASCII. Chcete-li například použít hvězdičku (*) jako literálový znak, použijte hodnotu `%2A`.

 Úplný seznam speciálních znaků k útěku následuje:

|Znak|Popis|
|---------------|-----------------|
|%|Znak procenta, který se používá k odkazování na metadata.|
|$|Znak dolaru, který se používá k odkazování na vlastnosti.|
|@|Na znaménko, slouží k odkazování na seznamy položek.|
|(|Otevřené závorky použité v seznamech.|
|)|Zavřít závorky, které se používají v seznamech.|
|;|Středník, oddělovač seznamu.|
|?|Otazník, zástupný znak při popisu specifikace souboru v části Zahrnout nebo vyloučit položku.|
|*|Hvězdička, zástupný znak při popisu specifikace souboru v části Zahrnout nebo vyloučit položku.|

> [!NOTE]
> V některých případech může být nutné uniknout dvojité uvozovky (") znaky, například při použití v rámci `Exec` úkolu.

## <a name="see-also"></a>Viz také

- [Postup: Escape speciální znaky v MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
