---
title: Uzly návrháře shaderů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f41d1d3d934ecd85ac36d24d704db561d42faa97
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293498"
---
# <a name="shader-designer-nodes"></a>Uzly návrháře shaderů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Články v této části dokumentace obsahují informace o různých uzlech návrháře shaderu, které vám umožní vytvářet grafické efekty.  
  
## <a name="nodes-and-node-types"></a>Uzlů a typy uzlů  
 Návrháře shaderu představuje vizuálních efektů jako graf. Tyto grafy jsou sestaveny z uzlů, které jsou speciálně vybrali a připojený v přesné způsoby, jak dosáhnout zamýšlený vliv. Každý uzel představuje určitý údaj nebo matematické funkce a připojení mezi nimi představují tok informací v rámci graf tak, aby byla výsledkem. Návrhář shaderu poskytuje šest typů jiný uzel – filtry uzly textury, parametry, konstanty, nástroj uzly a matematické uzly – a několik jednotlivé uzly patří do jednotlivých typů. V dalších článcích v této části jsou popsány těchto uzlů a typy uzlů, najdete v odkazech na konci tohoto dokumentu.  
  
## <a name="node-structure"></a>Uzel struktury  
 Všechny uzly se skládá z kombinace společné prvky. Každý uzel má aspoň jeden výstup terminálu na jeho pravé straně (s výjimkou uzlu konečnou barvu, která představuje výstup shaderu). Uzly, které představují výpočtů nebo vzorkovače textury mají vstupní terminály v jejich levostranné, ale uzly, které představují informace jste žádné vstupní terminály. Výstup terminály jsou připojené k zadání terminály přesunout informace z jednoho uzlu.  
  
### <a name="promotion-of-inputs"></a>Povýšení vstupy  
 Protože Shader Designer musí nakonec HLSL zdrojový kód tak, aby efekt je možné ve hře nebo aplikaci, podléhají uzlech návrháře shaderu propagace typu pravidla, která používá HLSL. Vzhledem k tomu, že grafický hardware primárně pracuje hodnoty s plovoucí desetinnou čárkou, zadejte povýšení mezi různými typy – třeba z `int` k `float`, nebo z `float` k `double`– neobvyklé. Místo toho protože hardwarovou akceleraci používá stejnou operaci i u více kusů informace najednou, jiný druh propagační akce může dojít, ve kterém je tak, aby odpovídala velikosti nejdelší vstupní posunut kratší počet vstupů. Jak je posunut závisí na typ vstupu a také na samotný operace:  
  
-   **Pokud je menší typu skalární hodnota, pak:**  
  
     Hodnota skalárních se replikují do vektoru, který se rovná velikosti větší vstup. Například skalární vstupní 5.0 stane vektor (5.0, 5.0, 5.0) po třech prvcích vektoru, bez ohledu na to, co je operace největší vstupu operace.  
  
-   **Pokud je menší typ vektoru a je operace násobení (\*, /, % a tak dále), pak:**  
  
     Hodnota vektoru se zkopíruje do přední elementů vektoru, který se rovná velikosti větší vstup a koncové prvky jsou nastaveny na 1.0. Například zadání vektorové (5.0, 5.0) bude vektor (5.0, 5.0, 1.0; 1,0) Pokud se násobí hodnotou vektor čtyřech prvcích. Toto nastavení zachovává třetí a čtvrtá prvky výstupu pomocí násobení identity 1.0.  
  
-   **Pokud menší typ vektoru a je operace sčítání (+,-, a tak dále), pak:**  
  
     Hodnota vektoru je zkopírována do přední prvky vektoru, který se rovná velikosti větší vstup a koncové prvky jsou nastaveny na 0,0. Například zadání vektorové (5.0, 5.0) bude vektor (5.0, 5.0, 0.0, 0.0) při přidání na čtyřech prvcích vektoru. Toto nastavení zachovává třetí a čtvrtá prvky výstupu pomocí additive identity 0,0.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Uzly konstanty](../designers/constant-nodes.md)|Popisuje uzly, které můžete použít k reprezentaci hodnoty literálu a interpolované vrcholu stavové informace ve výpočtech shaderu. Protože interpolovaných stav vrcholu a proto se liší pro každý pixel – každá instance pixel shader obdrží jinou verzi konstanty.|  
|[Uzly parametru](../designers/parameter-nodes.md)|Popisuje uzly, které můžete použít k reprezentaci kamery, vlastností materiálu, parametry osvětlení, čas a další informace o stavu aplikace ve výpočtech shaderu.|  
|[Uzly textury](../designers/texture-nodes.md)|Popisuje uzly, které můžete použít pro vzorkování různé typy textury a geometrie a k vytvoření nebo transformaci souřadnice textury v běžné způsoby.|  
|[Matematické uzly](../designers/math-nodes.md)|Popisuje uzly, které můžete použít k provedení algebraických, logika, trigonometrických a jiných matematických operací, které se mapují přímo na HLSL pokyny.|  
|[Uzly nástroje](../designers/utility-nodes.md)|Popisuje uzly, které můžete použít k provádění běžných výpočtů osvětlení a dalších běžných operací, které se nemapují přímo na HLSL pokyny.|  
|[Uzly filtru](../designers/filter-nodes.md)|Popisuje uzly, které můžete použít k provedení filtrování textur a filtrování barvu.|



