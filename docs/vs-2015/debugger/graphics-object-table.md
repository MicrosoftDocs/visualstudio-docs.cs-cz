---
title: Objekt grafiky tabulky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ba3ce8aa0727471ff4385792d85659fa2d208dc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809087"
---
# <a name="graphics-object-table"></a>Tabulka grafických objektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tabulka grafických objektů v grafické analýzy Visual Studia vám pomůže pochopit objekty Direct3D, které podporují rámec hře nebo aplikaci.  
  
 Toto je tabulka objektu:  
  
 ![Objekty Direct3D, která se vytvořila aplikace](../debugger/media/gfx-diag-demo-object-table-orientation.png "gfx_diag_demo_object_table_orientation")  
  
## <a name="understanding-the-graphics-object-table"></a>Principy tabulka grafických objektů  
 Pomocí objektu tabulky můžete analyzovat objekty Direct3D, které podporují vykreslování určitého snímku. Vykreslování problém s určitým objektem můžete přesně určit, zkoumání jejich vlastností a data (pomocí jiných nástrojů diagnostiky grafiky na vaše diagnostiky můžete zúžit seznam objektů, které nemusí být co očekáváte.) Když najdete problematický objektu, můžete použít vizualizaci, která je specifická pro její typ je prozkoumat – například můžete použít Editor obrázků pro zobrazení textury, nebo *vyrovnávací paměti Vizualizéru* Chcete-li zobrazit obsah vyrovnávací paměti.  
  
 Tabulka objektů podporuje kopírování a vkládání tak, aby pomocí jiného nástroje – například aplikace Microsoft Excel – prozkoumat její obsah.  
  
### <a name="graphics-object-table-format"></a>Formát tabulky objektů grafiky  
 Tabulka objektů zobrazí objekty Direct3D a prostředky, které podporují rámec, který je spojen s vybranou událost – například stavu objektů, vyrovnávací paměti, shadery, textury a další prostředky. Objekty, které byly vytvořeny v předchozím snímku, ale nejsou používány během zachyceného snímku jsou vynechány z tabulky objektů. Objekty, které nejsou zničeny předchozí události během zachyceného snímku jsou vynechány v následných událostech. Objekty, které nejsou nastavené na D3D10Device nebo D3D11DeviceContext se zobrazují jako šedou barvou. Objekty jsou zobrazeny ve formátu tabulky.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**identifikátor**|ID objektu.|  
|**Jméno**|Informace o konkrétní aplikaci, která byla nastavena na objekt pomocí funkce rozhraní Direct3D `SetPrivateData`– obvykle na další identifikační informace o objektu.|  
|**Typ**|Typ objektu.|  
|**Aktivní**|Zobrazí "*" pro objekt, který byl nastaven na D3D10Device nebo D3D11DeviceContext během zachyceného snímku.<br /><br /> To odpovídá na objekty, které se zobrazují jako šedý, ale poskytuje položku sloupec, který vám pomůže umožňující řazení tabulce objektů.|  
|**Velikost**|Velikost objektu v bajtech.|  
|**Formát**|Formát objektu. Například formát objektu textury nebo shader model shaderu objektu.|  
|**Šířka**|Šířka objektu textury. Nevztahuje se na jiné typy objektů.|  
|**Výška**|Výška objektu textury. Nevztahuje se na jiné typy objektů.|  
|**Hloubka**|Hloubka objektu 3D textury. Nejsou-li textura 3D, hodnota je 0. Nevztahuje se na jiné typy objektů.|  
|**MIPS**|Počet úrovní MIP, které obsahuje objekt textury. Nevztahuje se na jiné typy objektů.|  
|**ArraySize**|Počet elementů textury v poli textury. Rozsah je od 1 do horní omezení určené aktuální úroveň funkcí. Tato hodnota je pro – mapy krychle, 6krát počet předvypočtenou krychli jako pole.|  
|**Ukázky**|Počet multisamples na pixel.|  
  
## <a name="graphics-object-viewers"></a>Objekt grafiky prohlížeče  
 Chcete-li zobrazit podrobnosti o objektu, otevřete ji výběrem jeho názvu v tabulce objektů. Podrobnosti o objektu jsou zobrazeny v různých formátech, v závislosti na typu objektu. Například textury se zobrazí v prohlížeči textury a zobrazí se stav zařízení, jako je například kontextu zařízení D3D11 jako seznam formátovaný. Ujistěte se, různé verze rozhraní Direct3D využívají různé objekty a jsou často konkrétní vizualizéry pro nejdůležitější objekty jednotlivých verzí.  
  
 Tady je prohlížeč textur zobrazující obsah slučovací modul výstupu fázi zřetězení.  
  
 ![Zobrazení slučovací modul výstupu ve verzi preview textury](../debugger/media/gfx-diag-texture-preview.png "gfx_diag_texture_preview")  
  
### <a name="d3d12-command-list"></a>Seznam příkazů D3D12  
 Seznam příkazů v Direct3D 12 je objekt, který zaznamenává příkazy do přidělování příkazů tak, aby mohly být odeslány do GPU jako jeden požadavek. Seznamy příkazů obvykle provádět řadu nastavení stavu kreslení, zrušte a zkopírujte příkazy. Jsou to zvlášť důležité, protože se upřednostňuje vykreslování v Direct3D 12 a lze ji znovu použít mezi snímky a pomáhá tak zvýšit výkon. Podrobnosti o příkazu seznamu se zobrazí v novém okně dokumentu informace týkající se každá fáze kanálu zobrazí na vlastní kartě.  
  
### <a name="d3d12-pipeline-state-object-pso"></a>Objekt stavu kanálu D3D12 (PSO)  
 Objekt stavu kanálu v Direct3D 12 představuje podstatnou část stav GPU, včetně všech aktuálně shaderů sady a určitých objektů stav – funkce. Po vytvoření je neměnný kanál stav objektu – aplikaci můžete pouze změnit konfiguraci kanálu pomocí vazby objektu stavu jiném kanálu. PSO podrobnosti jsou zobrazeny v nové okno dokumentu s podrobnostmi o rozloženy hierarchicky konfiguraci kanálu.  
  
### <a name="d3d12-root-signature"></a>Kořenový podpis D3D12  
 V Direct3D 12 kořenový podpis definuje všechny prostředky, které jsou vázány na kanálu grafiky nebo výpočetní výkon a propojí seznamy příkazů s prostředky, které vyžaduje se shadery. Obvykle je jeden kořenový podpis pro grafické a jeden pro výpočetní prostředky v aplikaci. Kořenový podpis podrobnosti jsou zobrazeny v nové okno dokumentu s podrobnostmi o kořenový podpis rozloženy hierarchicky.  
  
### <a name="d3d12-resources"></a>Zdroje D3D12  
 V Direct3D 12 prostředků jsou pokrývající vše objekty, které poskytují data do kanálu vykreslování; To se liší od Direct3D11, které definuje mnoho objektů specifické pro různé typy a dimenze prostředků. Direct3D 12 prostředků může obsahovat data textury, data vrcholů, shader dat a další – dokonce můžou představovat cíle vykreslování, jako je například vyrovnávací paměť hloubky. Podrobnosti o prostředku Direct3D 12 se zobrazí v novém okně dokumentu; Analýza grafických použije příslušný prohlížeč pro obsah objektu prostředku, pokud je schopna určit její typ. Například objekt prostředku, který obsahuje data textury je zobrazen v prohlížeči textury, stejně jako objekt D3D11 Texture2D je.  
  
### <a name="device-context-object"></a>Objekt kontextu zařízení  
 V Direct3D 11 a Direct3D 10, kontextu zařízení (**kontextu zařízení D3D11** nebo **zařízením D3D10**) objekt je zvlášť důležité, protože obsahuje nejdůležitější informace o stavu a odkazuje na další objekty stavu, které jsou aktuálně nastaveny. Podrobnosti o kontextu zařízení se zobrazí v novém okně dokumentu a každou kategorii informací se zde zobrazí na vlastní kartě. Změny kontextu zařízení vyberete novou událost tak, aby odrážela aktuální stav zařízení.  
  
### <a name="buffer-object"></a>Objekt vyrovnávací paměti  
 Podrobnosti objektu vyrovnávací paměti (D3D11 vyrovnávací paměti nebo vyrovnávací paměti D3D10) se zobrazí v novém okně dokumentu, který představuje obsah vyrovnávací paměti v tabulce a poskytuje rozhraní pro změnu, jak se zobrazuje obsah vyrovnávací paměti. **Vyrovnávací paměti dat** tabulky podporuje kopírování a vkládání tak, aby pomocí jiného nástroje – například aplikace Microsoft Excel – prozkoumat její obsah. Obsah vyrovnávací paměti je interpretováno podle hodnoty **formátu** – pole se seznamem, který se nachází nahoře **vyrovnávací paměti dat** tabulky. V dialogovém okně můžete zadat složené data formátu, který se skládá z datových typů, které jsou uvedeny v následující tabulce. Například "float int", zobrazí se seznam struktur, které obsahují hodnotu s plovoucí desetinnou čárkou 32-bit, který je následován hodnotou 32bitové celé číslo se znaménkem. Složený datových formátů, které jste zadali, se přidají do pole se seznamem pro pozdější použití.  
  
 Můžete také přepínat **zobrazit posuny** zaškrtávací políčko Skrýt nebo Zobrazit posun každý prvek ve vyrovnávací paměti.  
  
|Typ|Popis|  
|----------|-----------------|  
|**float**|Hodnota s plovoucí desetinnou čárkou 32-bit.|  
|**float2**|Vektor, který obsahuje dva 32bitové hodnoty s plovoucí desetinnou čárkou.|  
|**float3**|Vektor, který obsahuje tři 32bitové hodnoty s plovoucí desetinnou čárkou.|  
|**FLOAT4**|Vektor, který obsahuje čtyři 32bitové hodnoty s plovoucí desetinnou čárkou.|  
|**byte**|Hodnota typu 8bitové celé číslo se znaménkem.|  
|**2 bajty**|Hodnota 16bitové celé číslo se znaménkem.|  
|**4 bajty.**|Hodnota 32bitové celé číslo se znaménkem. Stejné jako **int**.|  
|**8 bajtů**|64bitové celé číslo se znaménkem hodnoty. Stejné jako **int64**.|  
|**xbyte**|8bitové šestnáctková hodnota.|  
|**x2byte**|16bitové šestnáctkové hodnoty.|  
|**x4byte**|Šestnáctková hodnota 32-bit. Stejné jako **xint**.|  
|**x8byte**|64-bit šestnáctková hodnota. Stejné jako **xint64**.|  
|**ubyte**|Hodnota typu 8bitové celé číslo bez znaménka.|  
|**u2byte**|Hodnota 16bitové celé číslo bez znaménka.|  
|**u4byte**|Hodnota 32bitové celé číslo bez znaménka. Stejné jako **uint**.|  
|**u8byte**|Hodnota 64bitové celé číslo bez znaménka. Stejné jako **uint64**.|  
|**polovinu**|Hodnota s plovoucí desetinnou čárkou 16 bitů.|  
|**half2**|Vektor, který obsahuje dvě hodnoty s plovoucí desetinnou čárkou 16 bitů.|  
|**half3**|Vektor, který obsahuje tři 16bitové hodnoty s plovoucí desetinnou čárkou.|  
|**half4**|Vektor, který obsahuje čtyři 16bitové hodnoty s plovoucí desetinnou čárkou.|  
|**double**|Hodnota s plovoucí desetinnou čárkou 64bitové.|  
|**int**|Hodnota 32bitové celé číslo se znaménkem. Stejné jako **4bajtové**.|  
|**Int64**|64bitové celé číslo se znaménkem hodnoty. Stejné jako **8 bajtů**.|  
|**xint**|Šestnáctková hodnota 32-bit. Stejné jako **x4byte**.|  
|**xint64**|64-bit šestnáctková hodnota. Stejné jako **x8byte**.|  
|**uint**|Hodnota 32bitové celé číslo bez znaménka. Stejné jako **u4byte**.|  
|**UInt64**|Hodnota 64bitové celé číslo bez znaménka. Stejné jako **u8byte**.|  
|**bool**|Logická hodnota (`true` nebo `false`) hodnotu. Každá logická hodnota je reprezentován 32bitová hodnota.|  
  
## <a name="see-also"></a>Viz také  
 [Diagnostika grafiky (ladění grafiky DirectX)](../debugger/visual-studio-graphics-diagnostics.md)   
 [Návod: Chybějící objekty z důvodu stavu zařízení](../debugger/walkthrough-missing-objects-due-to-device-state.md)



