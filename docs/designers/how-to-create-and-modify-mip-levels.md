---
title: 'Postupy: Vytvoření a úprava úrovní MIP'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56fa2875b8a0893e55f7fc373b933b85b4fa8207
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72635528"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Postupy: vytváření a úprava úrovní MIP
Tento dokument ukazuje, jak použít **Editor obrázků** k vygenerování a úpravám *úrovní MIP pro úroveň minimálního* prostoru na úrovni obrazu (LOD).

## <a name="generating-mip-levels"></a>Generování úrovní MIP
*Mipmapping* je technika, která se používá ke zvýšení rychlosti vykreslování a omezení artefaktů aliasů pro objekty s texturou, a to pomocí předběžného výpočtu a uložení několika kopií textury v různých velikostech. Každá kopie, která se označuje jako úroveň MIP, je poloviční Šířka a výška předchozí kopie. Je-li textura vykreslena na povrchu objektu, je automaticky zvolena úroveň MIP, která je nejvhodnější pro oblast obrazovky povrchu textury. To znamená, že grafický hardware nemusí filtrovat textury s příliš velikostí, aby se zachovala konzistentní vizuální kvalita. I když náklady na paměť při ukládání úrovní MIP jsou přibližně 33 procent větší než původní textura, jejich zvýšení výkonu a kvality obrazu ho opravňují.

#### <a name="to-generate-mip-levels"></a>Generování úrovní MIP

1. Začněte základní texturou, jak je popsáno v tématu [Postupy: Vytvoření základní textury](../designers/how-to-create-a-basic-texture.md). Nejlepších výsledků dosáhnete, když zadáte texturu, která má šířku a výšku, které mají velikost mocniny dvě, například 256, 512, 1024 a tak dále.

2. Vygenerujte úrovně MIP. Na panelu nástrojů **režim editoru obrázků** vyberte **upřesnit**  > **nástroje**  > **Generovat MIPS**.

     Všimněte si, že tlačítka **Přejít na další úroveň MIP** a **Přejít na předchozí úroveň MIP** se teď zobrazují na panelu nástrojů **režim editoru obrázků** . Pokud se zobrazí okno **vlastnosti** , Všimněte si také, že vlastnosti **MIP úrovně MIP** a **počet úrovní MIP** se nyní zobrazí ve vlastnostech obrázku.

## <a name="modifying-mip-levels"></a>Úprava úrovní MIP
Chcete-li dosáhnout speciálních efektů nebo zvýšit kvalitu obrázku na konkrétní úroveň podrobností, můžete každou úroveň MIP upravit jednotlivě. Můžete například dát objektu texturu jiný vzhled na dálku (větší vzdálenost odpovídá menším úrovním MIP) nebo můžete zajistit, aby textury, které obsahují text nebo symboly, zůstaly čitelné i na menších úrovních MIP.

#### <a name="to-modify-an-individual-mip-level"></a>Úprava individuální úrovně MIP

1. Vyberte úroveň MIP, kterou chcete upravit. Na panelu nástrojů **režim editoru obrázků** můžete mezi úrovněmi MIP přejít pomocí tlačítka **Přejít na další úroveň MIP** a **Přejít na předchozí úroveň** MIP.

2. Po výběru úrovně MIP, kterou chcete upravit, můžete k úpravě použít nástroje pro kreslení beze změny obsahu jiných úrovní MIP. Nástroje pro kreslení jsou k dispozici na panelu nástrojů **Editor obrázků** . Po výběru nástroje můžete změnit jeho vlastnosti v okně **vlastnosti** . Informace o nástrojích pro kreslení a jejich vlastnostech naleznete v tématu [Editor obrázků](../designers/image-editor.md).

> [!NOTE]
> Pokud nepotřebujete měnit obsah jednotlivých úrovní MIP – jak můžete dosáhnout určitých účinků, doporučujeme, abyste vygenerovali mipmapy ze zdrojové textury v čase sestavení. To pomáhá zajistit, aby úrovně MIP zůstaly synchronizované se zdrojovou texturou, protože změny úrovně MIP se nešíří na jiné úrovně automaticky. Další informace o tom, jak generovat mipmapy v čase sestavení, naleznete v tématu [How to: Export Texture obsahující mipmapy](../designers/how-to-export-a-texture-that-contains-mipmaps.md).

## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření základní textury](../designers/how-to-create-a-basic-texture.md)