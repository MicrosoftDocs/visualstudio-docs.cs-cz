---
title: MSSCCPRJ. Soubor SCC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a04429bafb7da0b3d4922905bd712e82ba16a4ba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736157"
---
# <a name="mssccprjscc-file"></a>Soubor MSSCCPRJ.SCC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio řešení nebo projektu při umístění pod správou zdrojového kódu pomocí rozhraní IDE, rozhraní IDE obdrží dvou důležitých informací ze správy zdrojového kódu ve formě řetězce modulu plug-in. Tyto řetězce "AuxPath" a "Název_projektu", jsou neprůhledné rozhraní IDE, ale používají se modul plug-in provede najít řešení nebo projektu ve správě verzí. Rozhraní IDE obvykle získá tyto řetězce při prvním voláním [sccgetprojpath –](../extensibility/sccgetprojpath-function.md), a pak ukládá je do souboru řešení nebo projektu pro budoucí volání [sccopenproject –](../extensibility/sccopenproject-function.md). Když je vložená v soubory řešení a projektu, řetězce "AuxPath" a "Název_projektu" se neaktualizují automaticky, když uživatel větve, větve, nebo zkopíruje soubory řešení a projektu, které jsou ve správě verzí. Pokud chcete mít jistotu, že soubory řešení a projektu, přejděte na jejich správné umístění ve správě verzí, musí uživatelé ručně aktualizujte řetězce. Vzhledem k tomu, že řetězce mají být neprůhledný, nemusí být vždy jasné jak by měly být aktualizovány.  
  
 Plug-in správy zdrojových kódů se ukládání řetězců "AuxPath" a "Název_projektu" ve speciální soubor s názvem MSSCCPRJ vyhnout tomuto problému. SCC souboru. Je na straně klienta, místní soubor, který vlastní a spravuje pomocí modulu plug-in. Tento soubor je nikdy umístěn pod správou zdrojových kódů, ale generuje modul plug-in pro každý adresář, který obsahuje soubory se spravovanými zdroji. Pokud chcete zjistit, které soubory jsou soubory řešení a projektu sady Visual Studio, modul plug-in správy zdrojového kódu můžete porovnat standardní nebo uživatelem zadaný seznam přípon souborů. Jakmile IDE zjistí, že podporuje modul plug-in MSSCCPRJ. Soubor SCC přestane vložit "AuxPath" a "Název_projektu" řetězců do řešení a soubory projektu a jeho načteme MSSCCPRJ těchto řetězců. SCC souboru místo toho.  
  
 Zdrojový ovládací prvek modulu plug-in, který podporuje MSSCCPRJ. Soubor SCC musí dodržovat následující pokyny:  
  
-   Může existovat pouze jeden MSSCCPRJ. Soubor SCC jednotlivých adresářích.  
  
-   MSSCCPRJ. SCC soubor může obsahovat "AuxPath" a "Název_projektu" pro více souborů, které jsou pod správou zdrojových kódů v rámci zadaného adresáře.  
  
-   Řetězec "AuxPath" nesmí obsahovat uvozovky uvnitř. To může mít kolem něj uvozovky jako oddělovače (například pár dvojitých uvozovek slouží k označení prázdný řetězec). Integrované vývojové prostředí odstraní všechny nabídky z řetězce "AuxPath" přečtení z MSSCCPRJ. SCC souboru.  
  
-   Řetězec "Název_projektu" MSSCCPRJ. Soubor SCC musí odpovídat přesně řetězec vrácený z `SccGetProjPath` funkce. Pokud řetězec vrácený funkcí nemá uvozovky kolem něj zobrazí řetězec MSSCCPRJ. Soubor SCC musí mít uvozovky kolem něj a naopak.  
  
-   MSSCCPRJ. Vytvoří nebo aktualizuje pokaždé, když je umístěn soubor pod správou zdrojových kódů SCC soubor.  
  
-   Pokud MSSCCPRJ. Soubor SCC odstraní, poskytovatel by měl znovu při příštím provádí operaci správy zdrojových kódů týkající se tohoto adresáře.  
  
-   MSSCCPRJ. Soubor SCC musí striktně řídit definovaném formátu.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Obrázek MSSCCPRJ. Formát souboru SCC  
 Tady je ukázka MSSCCPRJ. Formát souboru SCC (čísla řádků jsou k dispozici pouze jako vodítko a by neměly být obsažené v těle souboru):  
  
 [Řádek 1] `SCC = This is a Source Code Control file`  
  
 [Řádek 2]  
  
 [Řádek 3] `[TestApp.sln]`  
  
 [Řádek 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Řádku 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Řádek 6]  
  
 [Řádek 7] `[TestApp.csproj]`  
  
 [Řádek 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Řádku 9] `SCC_Project_Name = "$/TestApp"`  
  
 První řádek stavy účel souboru a slouží jako podpis pro všechny soubory tohoto typu. Tento řádek by měl vypadat přesně to ve všech MSSCCPRJ. Soubory SCC:  
  
 `SCC = This is a Source Code Control file`  
  
 Následuje část nastavení pro každý soubor označené podle názvu souboru v hranatých závorkách. Tato část se opakuje pro každý soubor sledován. Tento řádek je příklad názvu souboru, konkrétně `[TestApp.csproj]`. Integrované vývojové prostředí očekává, že následující dva řádky. Ale nedefinuje styl z hodnot fronty definovaných. Proměnné jsou `SCC_Aux_Path` a `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Neexistuje žádný koncový oddělovač pro tento oddíl. Název souboru, stejně jako všechny literály, které se zobrazují v souboru, jsou definovány v souboru hlaviček scc.h. Další informace najdete v tématu [řetězce používají jako klíče pro vyhledání modulu Plug-in zdrojového ovládacího prvku](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek moduly plug-in zdrojového kódu](../extensibility/source-control-plug-ins.md)   
 [Řetězce, které slouží jako klíče pro vyhledání modulu plug-in pro správu zdrojového kódu](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)

