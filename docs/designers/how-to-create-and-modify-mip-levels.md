---
title: 'Postupy: Vytvoření a úprava úrovní MIP'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793d730df3942608451e7dbc329819b98c451973
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76113290"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Postup: Vytvoření a úprava úrovní MIP
Tento dokument ukazuje, jak pomocí **Editoru obrázků** generovat a upravovat *úrovně MIP* pro úroveň detailu (LoD) textury.

## <a name="generating-mip-levels"></a>Generování úrovní MIP
*Mipmapping* je technika, která se používá ke zvýšení rychlosti vykreslování a snížení artefaktů aliasingu na texturovaných objektech předvýpočtem a uložením několika kopií textury v různých velikostech. Každá kopie, která je známá jako úroveň MIP, je polovina šířky a výšky předchozí kopie. Když je textura vykreslena na povrchu objektu, automaticky se zvolí úroveň MIP, která nejvíce odpovídá ploše prostoru obrazovky texturovaného povrchu. To znamená, že grafický hardware nemusí filtrovat nadrozměrné textury, aby byla zachována konzistentní vizuální kvalita. Ačkoli náklady na paměť skladování úrovně MIP je asi o 33 procent více než původní textury sám, výkon a image-kvalitní zisky ospravedlnit.

#### <a name="to-generate-mip-levels"></a>Generování úrovní MIP

1. Začněte se základní texturou, jak je popsáno v [části Postup: Vytvoření základní textury](../designers/how-to-create-a-basic-texture.md). Nejlepších výsledků dosáhnete zadáním textury, která má šířku a výšku, které mají velikost 2, například 256, 512, 1024 a tak dále.

2. Vygenerujte úrovně MIP. Na panelu nástrojů **Režim editoru obrázků** zvolte **Rozšířené** > **nástroje** > **generovat Mips**.

     Všimněte si, že tlačítka **Přejít na další úroveň Mip** a **Přejít na předchozí úroveň Mip** se nyní zobrazují na panelu nástrojů **Režim editoru obrázků.** Pokud se zobrazí okno **Vlastnosti,** všimněte si také, že vlastnosti **Mip Level** a **Mip Level Count** jen pro čtení se nyní zobrazují ve vlastnostech obrazu.

## <a name="modifying-mip-levels"></a>Úprava úrovní MIP
Chcete-li dosáhnout speciálních efektů nebo zvýšit kvalitu obrazu na určitých úrovních detailů, můžete upravit každou úroveň MIP jednotlivě. Můžete například dát texturovanému objektu jiný vzhled ve vzdálenosti (větší vzdálenost odpovídá menším úrovním MIP) nebo můžete zajistit, aby textury obsahující text nebo symboly zůstaly čitelné i na menších úrovních MIP.

#### <a name="to-modify-an-individual-mip-level"></a>Úprava individuální úrovně MIP

1. Vyberte úroveň MIP, kterou chcete upravit. Na **panelu** nástrojů Režim editoru obrázků použijte tlačítka **Přejít na další úroveň MIP** a **Přejít na předchozí úroveň MIP,** abyste se pohybovali mezi úrovněmi MIP.

2. Po výběru úrovně MIP, kterou chcete upravit, můžete pomocí kreslicích nástrojů ji upravit bez změny obsahu jiných úrovní MIP. Kreslicí nástroje jsou k dispozici na panelu nástrojů **Editor obrázků.** Po výběru nástroje můžete změnit jeho vlastnosti v okně **Vlastnosti.** Informace o kreslicích nástrojích a jejich vlastnostech naleznete v [Editoru obrázků](../designers/image-editor.md).

> [!NOTE]
> Pokud nepotřebujete upravovat obsah jednotlivých úrovní MIP – jak byste mohli udělat k dosažení určitých efektů – doporučujeme generovat mipmapy ze zdrojové textury v době sestavení. To pomáhá zajistit, že úrovně MIP zůstanou synchronizovány se zdrojovou texturou, protože změny na úrovni MIP nejsou automaticky rozšířeny na jiné úrovně. Další informace o tom, jak generovat mipmapy v době sestavení, naleznete v [tématu How to: Export textury, která obsahuje mipmaps](../designers/how-to-export-a-texture-that-contains-mipmaps.md).

## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření základní textury](../designers/how-to-create-a-basic-texture.md)
