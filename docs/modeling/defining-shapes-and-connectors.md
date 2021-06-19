---
title: Definování obrazců a konektorů
description: Seznamte se s několika základními typy tvarů, které můžete použít k zobrazení informací v diagramu v jazyce specifickém pro doménu (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 622ff598ac2471814e51b0e268c12d40e726fb98
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385744"
---
# <a name="define-shapes-and-connectors"></a>Definování obrazců a konektorů

Existuje několik základních typů tvarů, které můžete použít k zobrazení informací v diagramu v jazyce specifickém pro doménu (DSL).

## <a name="basic-types-of-shapes-and-connectors"></a><a name="shapeTypes"></a> Základní typy obrazců a konektorů

Diagram DSL znázorňuje kolekci *obrazců* propojených spojnicemi nebo *konektory*. Obvykle, ale ne vždy:

- Tvary jsou viditelné znázornění prvků modelu.

- Konektory představují referenční relace.

- Diagram představuje kořenovou instanci modelu.

- Vkládání relací mezi prvky modelu se zobrazuje pomocí zachytění. Například prvky představující porty komponent jsou vloženy do komponenty.

Tyto vzory se nevynucuje, ale jsou silněji podporované. Při návrhu DSL mějte na paměti, že návrh vztahů vkládání by měl být ovlivněn tím, jak chcete model prezentovat na obrazovce. Naproti tomu referenční relace by měly odrážet koncepty vaší obchodní domény.

K dispozici jsou následující typy tvarů:

|Typ obrazce|Description|
|-|-|
|Tvar geometrie|Obdélníkový nebo eliptický tvar pro obecné účely. Dekorátory textu a ikon můžete zobrazit na konkrétních pozicích vzhledem k hranicím obrazce. Tvary můžete také vnořit do tvarů geometrie.|
|Tvar přihrádky|Obdélník obsahující záhlaví a oddíly, jako je třída UML. Každá přihrádka může obsahovat seznam textových řádků.<br /><br /> Řádky obvykle představují prvky vložené pod elementem reprezentovaný tvarem. Můžete například vytvořit DSL ze šablony řešení diagramů tříd.|
|Tvar obrázku|Tvar, který zobrazuje obrázek.|
|Tvar portu|Malý obdélník navržený pro připojení k obrysu jiného tvaru. Obvykle se používá v modelech komponent.<br /><br /> Prvek modelu reprezentovaný portem je obvykle vložen pod element reprezentovaný nadřazeným tvarem. Můžete například vytvořit DSL pomocí šablony řešení Komponenty.<br /><br /> Tvar portu se standardně může po stranách nadřazeného portu posunovat. Můžete definovat pravidlo meze, které ho omezí na konkrétní pozici.<br /><br /> Díky velmi malému a průhlednému tvaru portu ho můžete použít k poskytnutí pevného spojovacího bodu na povrchu nadřazeného tvaru.|
|Plavecký drah|Dráhy rozděluje diagram do vodorovných nebo svislých segmentů. Dráha vždy zůstává pod ostatními tvary v diagramu.<br /><br /> Prvky modelu dráhy jsou obvykle nadřazeny v kořenovém adresáři modelu a ostatní prvky jsou nad nimi nadřazené. Můžete například vytvořit DSL ze šablony řešení toku úloh.|
|Konektory|Čáry nakreslené mezi tvary obvykle představují referenční relace. Můžete nastavit možnosti pro přímé nebo přímé připojení konektoru a pro různé typy šipek.|

## <a name="shape-inheritance"></a>Dědičnost obrazce

Tvar může dědit z jiného tvaru. Tvary ale musí být stejného druhu. Z tvaru geometrie může například dědit pouze tvar geometrie. Zděděné tvary mají oddíly a dekorátory svého základního tvaru. Konektory mohou dědit z konektorů.
