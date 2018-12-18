---
title: Grafika objektu tabulky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.datavisualizer
- vs.graphics.objecttable
- vs.graphics.bufferviewer
ms.assetid: f48f62d9-16ff-4a2e-8c01-5cbe99513788
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d58c219069efcc98fccaa52dff5bd156212ea64d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31477762"
---
# <a name="graphics-object-table"></a>Tabulka grafických objektů
Tabulka grafických objektů v aplikaci Visual Studio analýza grafických vám pomůže pochopit Direct3D – objekty, které podporují rámec hry nebo aplikace.  
  
 Toto je tabulka objektu:  
  
 ![Direct3D – objekty, které byly vytvořeny pomocí aplikace](media/gfx_diag_demo_object_table_orientation.png "gfx_diag_demo_object_table_orientation")  
  
## <a name="understanding-the-graphics-object-table"></a>Principy tabulka grafických objektů  
 Pomocí objektu tabulky můžete analyzovat Direct3D – objekty, které podporují vykreslování určitého snímku. Vykreslování problém s určitým objektem lze přesně určit tak, že prověří jeho vlastnosti a data (pomocí jiných nástrojů diagnostiky grafiky dříve v vaší diagnostiku můžete zúžit seznam objektů, které nemusí být očekávat.) Pokud jste nalezen objekt problematické, můžete použít vizualizace, která je specifická pro její typ a zkontrolujte ji – například Editor obrázků můžete zobrazit textury, nebo *vizualizér vyrovnávací paměti* zobrazíte obsah vyrovnávací paměti.  
  
 Objekt tabulka podporuje kopírování a vkládání, aby pomocí jiného nástroje – například aplikace Microsoft Excel – a zkontrolujte jeho obsah.

 Kromě toho můžete použít **typ** rozevírací seznam v horní části levého horního rohu k přepnutí zobrazení objekty typu **vyrovnávací paměti**, **shadery** nebo **textury**, nebo všechny tyto položky najednou.  Do vyhledávacího pole můžete použít také v pravém horním rohu najít konkrétní řádky ve všech dat, která se zobrazí.  Například můžete vyhledat pro *D32_FLOAT* v seznamu vyhledejte všechny instance objektů tohoto formátu.
  
### <a name="graphics-object-table-format"></a>Formát grafiky tabulce objektů.  
 V tabulce objekt zobrazí Direct3D – objekty a prostředky, které podporují rámce, který je spojen s vybrané události – například stavu objektů vyrovnávací paměti, shadery textury a dalším prostředkům. Objekty, které byly vytvořeny v předchozím snímku, ale nejsou používány během zaznamenané rámečku byly vynechány z tabulky objektu. Objekty, které byly zlikvidovány v předchozích událostech během zaznamenané rámečku byly vynechány v následných událostech. Objekty, které nejsou nastaveny na D3D10Device nebo D3D11DeviceContext zobrazují jako šedou barvou. Objekty jsou zobrazeny ve formátu tabulky.  
  
|Sloupec|Popis|  
|------------|-----------------|  
|**Identifikátor**|ID objektu.|  
|**Jméno**|Informace specifické pro aplikace, které se nastavit u objektu pomocí funkce Direct3D – `SetPrivateData`– obvykle zajistit další identifikační informace o objektu.|  
|**Typ**|Typ objektu.|  
|**Aktivní**|Zobrazí "*" pro objekt, který byl nastaven na D3D10Device nebo D3D11DeviceContext během zaznamenané rámečku.<br /><br /> To odpovídá objekty, které se zobrazují jako šedé text, ale poskytuje položku sloupců, která můžete použít ke zvýšení řazení tabulce objektů.|  
|**Velikost**|Velikost objektu v bajtech.|  
|**Formát**|Formát objektu. Například formát objekt texture nebo model shaderu shaderu objektu.|  
|**Šířka**|Šířka objektu texture. Nevztahuje se na jiné typy objektů.|  
|**Výška**|Výška objektu texture. Nevztahuje se na jiné typy objektů.|  
|**Hloubka**|Hloubka 3D texture objektu. Pokud texturou není 3D, hodnota je 0. Nevztahuje se na jiné typy objektů.|  
|**MIPS**|Počet úrovní MIP, které obsahuje objekt texture. Nevztahuje se na jiné typy objektů.|  
|**ArraySize**|Počet textury v poli texture. Rozsah je od 1 do horní mez definované aktuální úroveň funkce. Pro datové krychle mapě je tato hodnota 6krát počet mapy datové krychle v poli.|  
|**Ukázky**|Počet multisamples na pixel.|  
  
## <a name="graphics-object-viewers"></a>Objekt grafiky prohlížečů  
 Chcete-li zobrazit podrobnosti o objektu, otevřete výběrem jeho název v tabulce objektů. V různých formátech, v závislosti na typu objektu, se zobrazí podrobnosti o objektu. Například textury se zobrazí pomocí prohlížeče texture a stavu zařízení, jako je například D3D11 kontextu zařízení se zobrazí jako formátovaný seznam. Ujistěte se, různých verzích Direct3D – využívají různé objekty a jsou často konkrétní vizualizérech pro nejdůležitější objekty jednotlivých verzí.  
  
 Zde je texture prohlížeč zobrazující obsah fáze kanálu fúze výstup.  
  
 ![Ve verzi preview texture zobrazení výstupu fúze](media/gfx_diag_texture_preview.png "gfx_diag_texture_preview")  
  
### <a name="d3d12-command-list"></a>Seznam příkazů D3D12  
 V Direct3D – 12 příkaz seznamu je objekt, který zaznamenává příkazy do příkazu přidělování, tak, aby mohly být odeslány na grafický procesor s jako jeden požadavek. Příkaz seznamy obvykle provést řadu nastavení stavu kreslení, zrušte a zkopírujte příkazy. Jsou zvlášť důležité vzhledem k tomu, že jsou preferovanou metodu vykreslování v Direct3D – 12 a můžete znovu použít mezi rámce za účelem zvýšení výkonu. Příkaz seznamu podrobnosti jsou zobrazeny v okno Nový dokument s informace týkající se každá fáze kanálu uvedené na vlastní kartě.  
  
### <a name="d3d12-pipeline-state-object-pso"></a>Objekt stavu kanálu D3D12 (PSO)  
 Objekt stavu kanálu v Direct3D – 12 představuje podstatnou část GPU stavu, včetně všechny aktuálně shadery sady a určitých objektů – funkce stavu. Po vytvoření se nedá změnit objekt stavu profilace – aplikace můžete změnit konfiguraci kanálu pouze pomocí vytvoření vazby na jiném kanálu stavu objekt. V novém okně dokumentu, podrobné informace o této konfiguraci kanálu nastíněny hierarchicky jsou zobrazené podrobnosti PSO.  
  
### <a name="d3d12-root-signature"></a>Podpis kořenové D3D12  
 V Direct3D – 12 podpis kořenové definuje všechny prostředky, které jsou vázány na kanál grafiky nebo výpočetní a prostředky, které vyžaduje shadery odkazuje příkaz seznamy. Obvykle není jeden kořenový podpis pro grafiky a jeden pro výpočty v aplikaci. V novém okně dokumentu, podrobné informace o této kořenové podpis nastíněny hierarchicky jsou zobrazené podrobnosti kořenové podpis.  
  
### <a name="d3d12-resources"></a>D3D12 prostředky  
 V Direct3D – 12 jsou prostředky catch všechny objekty, které poskytují data do kanálu vykreslování; Tím se liší od Direct3D11, která definovaná mnoho objektů specifické pro různé typy a dimenze prostředků. Direct3D – 12 prostředků může obsahovat texture data, vrchol dat, shaderu dat a další – i může představovat cíle vykreslení například hloubka vyrovnávací paměti. Podrobnosti prostředku Direct3D – 12 jsou zobrazeny v novém okně dokumentu; Analýza grafických použije příslušný prohlížeč pro obsah objektu prostředků, pokud to bude možné určit jeho typ. Například objekt prostředku, který obsahuje texture data zobrazí pomocí prohlížeče texture, stejně jako objekt D3D11 Texture2D je.  
  
### <a name="device-context-object"></a>Objekt kontextu zařízení  
 Direct3D – 11 a Direct3D – 10, kontextu zařízení (**kontextu zařízení D3D11** nebo **D3D10 zařízení**) objekt je obzvláště důležité, protože drží nejdůležitější informace o stavu, a obsahuje odkazy na další Stav objekty, které jsou aktuálně nastavené. Podrobnosti o kontextu zařízení se zobrazí v novém okně dokumentu, a každou kategorii informace se zobrazí existuje na vlastní kartě. Změny zařízení kontextu, když je vybrán novou událost odráží aktuální stav zařízení.  
  
### <a name="buffer-object"></a>Objekt vyrovnávací paměti  
 Podrobnosti objektu vyrovnávací paměti (D3D11 vyrovnávací paměti nebo vyrovnávací paměti D3D10) se zobrazí v novém okně dokumentu, která představuje vyrovnávací paměti obsah v tabulce a poskytuje rozhraní pro změnu zobrazení obsah vyrovnávací paměti. **Vyrovnávací paměť dat** tabulky podporuje kopírování a vkládání, aby pomocí jiného nástroje – například aplikace Microsoft Excel – a zkontrolujte jeho obsah. Obsah vyrovnávací paměti je interpretovat v souladu hodnotu **formátu** – pole se seznamem, který je umístěn výše **vyrovnávací paměť dat** tabulky. V dialogovém okně můžete zadat složené data formátu, který se skládá z datových typů, které jsou uvedeny v následující tabulce. Například "float int", zobrazí se seznam struktury, které obsahují hodnotu s plovoucí desetinnou čárkou 32bitová verze a potom podle hodnoty 32bitové celé číslo se znaménkem. Složené datové formáty, které jste zadali, se přidají do pole se seznamem pro pozdější použití.  
  
 Můžete také přepnutí **zobrazit posune** políčko skrytí nebo zobrazení posun každý prvek ve vyrovnávací paměti.  
  
|Typ|Popis|  
|----------|-----------------|  
|**float**|Hodnota s plovoucí desetinnou čárkou 32-bit.|  
|**float2**|Vektor, který obsahuje dva 32bitové hodnoty s plovoucí desetinnou čárkou.|  
|**float3**|Vektor, který obsahuje tři 32bitové hodnoty s plovoucí desetinnou čárkou.|  
|**FLOAT4**|Vektor, který obsahuje čtyři 32bitové hodnoty s plovoucí desetinnou čárkou.|  
|**byte**|Hodnota typu 8bitové celé číslo se znaménkem.|  
|**2 bajtů**|Hodnota 16bitové celé číslo se znaménkem.|  
|**4bajtové**|Hodnota, 32bitové celé číslo se znaménkem. Stejné jako **int**.|  
|**na 8 bajtů**|Hodnota 64bitové celé číslo se znaménkem. Stejné jako **int64**.|  
|**xbyte**|8bitové šestnáctkové hodnoty.|  
|**x2byte**|16bitové šestnáctkové hodnoty.|  
|**x4byte**|32bitové šestnáctkové hodnoty. Stejné jako **xint**.|  
|**x8byte**|64bitová verze šestnáctkové hodnoty. Stejné jako **xint64**.|  
|**ubyte**|Hodnota typu 8bitové celé číslo bez znaménka.|  
|**u2byte**|Hodnota 16bitové celé číslo bez znaménka.|  
|**u4byte**|Hodnota, 32bitové celé číslo bez znaménka. Stejné jako **Celé_číslo**.|  
|**u8byte**|Hodnota 64bitové celé číslo bez znaménka. Stejné jako **uint64**.|  
|**polovinu**|Hodnota s plovoucí desetinnou čárkou 16 bitů.|  
|**half2**|Vektor, který obsahuje dvě hodnoty s plovoucí desetinnou čárkou 16 bitů.|  
|**half3**|Vektor, který obsahuje tři hodnoty s plovoucí desetinnou čárkou 16 bitů.|  
|**half4**|Vektor, který obsahuje čtyři 16 bitů s plovoucí desetinnou čárkou.|  
|**double**|Hodnota s plovoucí desetinnou čárkou 64-bit.|  
|**int**|Hodnota, 32bitové celé číslo se znaménkem. Stejné jako **4bajtové**.|  
|**Int64**|Hodnota 64bitové celé číslo se znaménkem. Stejné jako **8bajtová**.|  
|**xint**|32bitové šestnáctkové hodnoty. Stejné jako **x4byte**.|  
|**xint64**|64bitová verze šestnáctkové hodnoty. Stejné jako **x8byte**.|  
|**uint**|Hodnota, 32bitové celé číslo bez znaménka. Stejné jako **u4byte**.|  
|**UInt64**|Hodnota 64bitové celé číslo bez znaménka. Stejné jako **u8byte**.|  
|**bool**|Logická hodnota (`true` nebo `false`) hodnotu. Každý logická hodnota je reprezentována 32bitovou hodnotu.|  
  
## <a name="see-also"></a>Viz také  
 [Diagnostika grafiky (ladění grafiky DirectX)](visual-studio-graphics-diagnostics.md)   
 [Návod: Chybějící objekty z důvodu stavu zařízení](walkthrough-missing-objects-due-to-device-state.md)