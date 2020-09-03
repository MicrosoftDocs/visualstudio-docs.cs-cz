---
title: Tabulka objektů grafiky | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea80420b2146bd8c604a95d71012009dcb940ef5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72735438"
---
# <a name="graphics-object-table"></a>Tabulka grafických objektů
Tabulka objekt grafiky v analýze grafiky sady Visual Studio pomáhá pochopit objekty Direct3D, které podporují rámec vaší hry nebo aplikace.

 Toto je tabulka objektů:

 ![Direct3D objekty, které vytvořila aplikace](media/gfx_diag_demo_object_table_orientation.png "gfx_diag_demo_object_table_orientation")

## <a name="understanding-the-graphics-object-table"></a>Porozumění tabulce objekt grafiky
 Pomocí tabulky objektů můžete analyzovat objekty Direct3D, které podporují vykreslování konkrétního snímku. Můžete určit problém vykreslování konkrétního objektu, a prozkoumáním jeho vlastností a dat (pomocí dalších Diagnostika grafiky nástrojů dříve v diagnostice můžete zúžit seznam objektů, které nemusí být očekávaným způsobem.) Po nalezení problematického objektu můžete použít vizualizaci, která je specifická pro jeho typ, a ověřit ho – například můžete použít Editor obrázků k zobrazení textur nebo *Vizualizér vyrovnávací paměti* pro zobrazení obsahu vyrovnávací paměti.

 Tabulka objektů podporuje kopírování a vkládání, takže můžete použít jiný nástroj, například Microsoft Excel – k prohlédnutí jeho obsahu.

 Kromě toho můžete pomocí rozevíracího seznamu **typ** v levém horním rohu přepnout zobrazování objektů typu **vyrovnávací paměti**, **shaderů** nebo **textur**nebo všechny tyto položky najednou.  Můžete také použít vyhledávací pole v pravém horním rohu a vyhledat konkrétní řádky napříč všemi zobrazenými daty.  Můžete například vyhledat *D32_FLOAT* a najít všechny instance objektů tohoto formátu v seznamu.

### <a name="graphics-object-table-format"></a>Formát tabulky objektů grafiky
 Tabulka objektů zobrazuje objekty a prostředky Direct3D, které podporují rámec přidružený k vybrané události – například stavové objekty, vyrovnávací paměti, shadery, textury a další prostředky. Objekty, které byly vytvořeny v předchozím snímku, ale nejsou použity během zachyceného rámce, jsou vynechány v tabulce objektů. Objekty, které byly zničeny předchozími událostmi během zachyceného rámce, jsou v následných událostech vynechány. Objekty, které nejsou nastavené na D3D10Device nebo D3D11DeviceContext, se zobrazují jako šedý text. Objekty se zobrazí ve formátu tabulky.

|Sloupec|Popis|
|------------|-----------------|
|**Identifikátor**|ID objektu.|
|**Name**|Informace specifické pro aplikaci, které byly nastaveny u objektu pomocí funkce Direct3D `SetPrivateData` – obvykle k poskytnutí dalších identifikačních informací o objektu.|
|**Typ**|Typ objektu.|
|**Aktivní**|Zobrazí "*" pro objekt, který byl nastaven na D3D10Device nebo D3D11DeviceContext během zachyceného snímku.<br /><br /> To odpovídá objektům, které se zobrazují jako šedý text, ale poskytuje položku sloupce, kterou můžete použít k tomu, abyste mohli seřadit tabulku objektů.|
|**Velikost**|Velikost objektu v bajtech|
|**Formát**|Formát objektu Například formát objektu textury nebo model shaderu objektu shader.|
|**Width (Šířka)**|Šířka objektu textury. Nevztahuje se na jiné typy objektů.|
|**Height (Výška)**|Výška objektu textury. Nevztahuje se na jiné typy objektů.|
|**Úrovní**|Hloubka 3D objektu textury. Pokud textura není 3-D, hodnota je 0. Nevztahuje se na jiné typy objektů.|
|**MIPS**|Počet úrovní MIP, které má objekt textury. Nevztahuje se na jiné typy objektů.|
|**ArraySize**|Počet textur v poli textury. Rozsah je od 1 do horní meze definované aktuální úrovní funkce. Pro mapu krychle je tato hodnota 6 časů počtu mapování krychle v poli.|
|**ukázky**|Počet více vzorků na pixel.|

## <a name="graphics-object-viewers"></a>Prohlížeč objektů grafiky
 Chcete-li zobrazit podrobnosti o objektu, otevřete jej výběrem jeho názvu v tabulce objektů. Podrobnosti o objektu jsou zobrazeny v různých formátech v závislosti na typu objektu. Například textury se zobrazují pomocí prohlížeče textur a stav zařízení, jako je například D3D11, kontext zařízení se zobrazuje jako formátovaný seznam. Různé verze technologie Direct3D využívají různé objekty a existují často konkrétní vizualizace pro nejdůležitější objekty každé verze.

 Tady je prohlížeč textury, který zobrazuje obsah fáze výstupního kanálu fúze.

 ![Náhled textury zobrazující sloučení výstupu](media/gfx_diag_texture_preview.png "gfx_diag_texture_preview")

### <a name="d3d12-command-list"></a>Seznam příkazů D3D12
 V Direct3D 12 je seznam příkazů objekt, který zaznamenává příkazy do přidělování příkazů, aby je bylo možné odeslat do GPU jako jediný požadavek. Seznamy příkazů obvykle provádějí sérii příkazů pro nastavení stavu, kreslení, vymazání a kopírování. Jsou obzvláště důležité, protože jsou upřednostňovanou metodou vykreslování v Direct3D 12 a je možné je znovu použít mezi snímky, abyste mohli zvýšit výkon. Podrobnosti o seznamu příkazů se zobrazí v novém okně dokumentu a informace související s jednotlivými fázemi kanálu jsou uvedeny na vlastní kartě.

### <a name="d3d12-pipeline-state-object-pso"></a>Objekt stavu kanálu D3D12 (PSO)
 V Direct3D 12 objekt stavu kanálu představuje významnou část stavu GPU, včetně všech aktuálně nastavených shaderů a určitých objektů stavu s pevnou funkcí. Po vytvoření objekt stavu kanálu není proměnlivý – aplikace může změnit konfiguraci kanálu jenom tak, že vytvoří vazbu jiného objektu stavu kanálu. Podrobnosti o PSO se zobrazí v novém okně dokumentu s podrobnostmi o konfiguraci kanálu, která je rozložená hierarchicky.

### <a name="d3d12-root-signature"></a>Kořenová signatura D3D12
 V Direct3D 12 definuje kořenový podpis všechny prostředky, které jsou svázané s grafikou nebo výpočetním kanálem, a propojuje seznamy příkazů s prostředky, které shader vyžaduje. Obvykle je k dispozici jeden kořenový podpis grafiky a jeden pro výpočty v aplikaci. Podrobnosti o kořenovém podpisu se zobrazí v novém okně dokumentu s podrobnostmi o kořenovém podpisu, který je rozložený hierarchicky.

### <a name="d3d12-resources"></a>Prostředky D3D12
 V Direct3D 12 jsou prostředky zachytávání – všechny objekty, které poskytují data do kanálu vykreslování; To je na rozdíl od Direct3D11, který definoval mnoho konkrétních objektů pro různé druhy a dimenze prostředků. Prostředek Direct3D 12 může obsahovat data textury, data vrcholu, data shaderu a další – můžou dokonce představovat cíle vykreslování, jako je například vyrovnávací paměť hloubky. Podrobnosti o prostředku Direct3D 12 se zobrazí v novém okně dokumentu. Analýza grafiky bude používat vhodný prohlížeč pro obsah objektu prostředku, pokud je možné určit jeho typ. Například objekt prostředku, který obsahuje data textury, se zobrazí pomocí prohlížeče textur, podobně jako objekt D3D11 Texture2D je.

### <a name="device-context-object"></a>Objekt kontextu zařízení
 V rozhraních Direct3D 11 a Direct3D 10 je kontext zařízení (**kontext zařízení d3d11** nebo **zařízení d3d10**) obzvláště důležitý, protože obsahuje nejdůležitější informace o stavu a odkazuje na objekty s dalšími stavy, které jsou aktuálně nastaveny. Podrobnosti o kontextu zařízení se zobrazí v novém okně dokumentu a každá kategorie informací se zobrazí na vlastní kartě. Kontext zařízení se změní, když je vybrána nová událost, aby odrážela aktuální stav zařízení.

### <a name="buffer-object"></a>Buffer – objekt
 Podrobnosti o objektu vyrovnávací paměti (vyrovnávací paměť D3D11 nebo vyrovnávací paměť D3D10) se zobrazí v novém okně dokumentu, které prezentuje obsah vyrovnávací paměti v tabulce, a poskytuje rozhraní pro změnu způsobu zobrazení obsahu vyrovnávací paměti. Tabulka **dat vyrovnávací paměti** podporuje kopírování a vkládání, takže můžete použít jiný nástroj, například Microsoft Excel – k prohlédnutí jeho obsahu. Obsah vyrovnávací paměti je interpretován podle hodnoty pole se seznamem **Formát** , který je umístěn nad tabulkou **dat vyrovnávací paměti** . Do pole můžete zadat formát složených dat, který se skládá z datových typů, které jsou uvedeny v následující tabulce. Například "float int" zobrazí seznam struktur, které obsahují 32 hodnoty s plovoucí desetinnou čárkou následovanou 32-bit signed integer. Složené formáty dat, které jste zadali, jsou přidány do pole se seznamem pro pozdější použití.

 Můžete také přepnout zaškrtávací políčko **Zobrazit posunutí** pro skrytí nebo zobrazení posunutí jednotlivých prvků ve vyrovnávací paměti.

|Typ|Popis|
|----------|-----------------|
|**float**|Hodnota 32-bit s plovoucí desetinnou čárkou.|
|**float2**|Vektor, který obsahuje 2 32 hodnot s plovoucí desetinnou čárkou.|
|**float3**|Vektor, který obsahuje 3 32 hodnot s plovoucí desetinnou čárkou.|
|**float4**|Vektor, který obsahuje 4 32 hodnot s plovoucí desetinnou čárkou.|
|**bytové**|8bitové celočíselné hodnoty se znaménkem.|
|**2byte**|16bitová celočíselná hodnota se znaménkem.|
|**4byte**|Hodnota se znaménkem pro celé číslo v hodnotě 32. Stejné jako **int**.|
|**8byte**|Hodnota se znaménkem pro celé číslo v hodnotě 64. Totéž jako **Int64**.|
|**xbyte**|16bitová hexadecimální hodnota.|
|**x2byte**|16bitová hexadecimální hodnota.|
|**x4byte**|Bitová hexadecimální hodnota 32. Stejné jako **xint**.|
|**x8byte**|Bitová hexadecimální hodnota 64. Stejné jako **xint64**.|
|**ubyte**|Hodnota 8 bitů unsigned integer.|
|**u2byte**|16bitová hodnota unsigned integer.|
|**u4byte**|Hodnota 32 unsigned integer. Stejné jako **uint**.|
|**u8byte**|Hodnota 64 unsigned integer. Stejné jako **UInt64**.|
|**poloduplexní**|16bitová hodnota s plovoucí desetinnou čárkou.|
|**half2**|Vektor, který obsahuje 2 16 hodnot s plovoucí desetinnou čárkou.|
|**half3**|Vektor, který obsahuje 3 16 hodnot s plovoucí desetinnou čárkou.|
|**half4**|Vektor, který obsahuje 4 16 hodnot s plovoucí desetinnou čárkou.|
|**double**|Hodnota 64-bit s plovoucí desetinnou čárkou.|
|**int**|Hodnota se znaménkem pro celé číslo v hodnotě 32. Stejné jako **4byte**.|
|**Int64**|Hodnota se znaménkem pro celé číslo v hodnotě 64. Stejné jako **8byte**.|
|**xint**|Bitová hexadecimální hodnota 32. Stejné jako **x4byte**.|
|**xint64**|Bitová hexadecimální hodnota 64. Stejné jako **x8byte**.|
|**uint**|Hodnota 32 unsigned integer. Stejné jako **u4byte**.|
|**UInt64**|Hodnota 64 unsigned integer. Stejné jako **u8byte**.|
|**bool**|Logická hodnota ( `true` nebo `false` ). Každá logická hodnota je reprezentována 32 hodnotou.|

## <a name="see-also"></a>Viz také
- [Diagnostika grafiky (Ladění grafiky DirectX)](visual-studio-graphics-diagnostics.md)
- [Návod: Chybějící objekty z důvodu stavu zařízení](walkthrough-missing-objects-due-to-device-state.md)