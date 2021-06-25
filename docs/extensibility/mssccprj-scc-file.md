---
title: MSSCCPRJ. Soubor SCC | Microsoft Docs
description: Přečtěte si o MSSCCPRJ. Soubor SCC, což je místní soubor na straně klienta používaný modulem plug-in pro správu zdrojového kódu, který spolupracuje se sadou Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e006e4462522f4c464f40e0656dcef4d32c85fb7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899248"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Soubor SCC
Při umístění řešení nebo projektu sady Visual Studio pod správu zdrojového kódu pomocí integrovaného vývojového prostředí (IDE) obdrží dva klíčové části informací. Informace pocházejí z modulu plug-in správy zdrojových kódů ve formě řetězců. Tyto řetězce "AuxPath" a "ProjName" jsou neprůhledné na integrované vývojové prostředí (IDE), ale jsou používány modulem plug-in k vyhledání řešení nebo projektu ve správě verzí. Rozhraní IDE obvykle tyto řetězce načítá při volání [SccGetProjPath](../extensibility/sccgetprojpath-function.md)a pak je uloží do souboru řešení nebo projektu pro budoucí volání [SccOpenProject](../extensibility/sccopenproject-function.md). Při vložení do souborů řešení a projektu se řetězce "AuxPath" a "ProjName" automaticky neaktualizují, pokud je uživatel větví, rozvětvení nebo kopíruje řešení a soubory projektu, které jsou ve správě verzí. Chcete-li zajistit, aby soubory řešení a projektu odkazovaly na správné místo v řízení verze, uživatelé musí ručně aktualizovat řetězce. Vzhledem k tomu, že jsou řetězce určeny jako neprůhledné, nemusí vždy být jasné, jak by se měly aktualizovat.

 Modul plug-in správy zdrojových kódů se může vyhnout tomuto problému uložením řetězců "AuxPath" a "ProjName" do speciálního souboru, který se nazývá soubor *MSSCCPRJ. SCC* . Jedná se o místní soubor na straně klienta, který je vlastněn a udržován modulem plug-in. Tento soubor není nikdy umístěn pod správou zdrojových kódů, ale je vygenerován modulem plug-in pro každý adresář, který obsahuje soubory se spravovanými zdroji. Aby bylo možné určit, které soubory jsou soubory řešení a projektu sady Visual Studio, modul plug-in správy zdrojových kódů může porovnat přípony souborů se standardním nebo uživatelem zadaným seznamem. Jakmile rozhraní IDE zjistí, že modul plug-in podporuje soubor *MSSCCPRJ. SCC* , přestane vkládat řetězce "AuxPath" a "ProjName" do souborů řešení a projektu a místo toho tyto řetězce přečte ze souboru *MSSCCPRJ. SCC* .

 Modul plug-in správy zdrojového kódu, který podporuje soubor *MSSCCPRJ. SCC* , musí splňovat následující pokyny:

- Pro každý adresář může existovat pouze jeden soubor *MSSCCPRJ. SCC* .

- Soubor *MSSCCPRJ. SCC* může obsahovat "AuxPath" a "ProjName" pro více souborů, které jsou pod správou zdrojových kódů v daném adresáři.

- Řetězec "AuxPath" nesmí obsahovat v něm uvozovky. Může mít uvozovky kolem sebe jako oddělovače (například k označení prázdného řetězce lze použít dvojici dvojitých uvozovek). Rozhraní IDE při čtení ze souboru *MSSCCPRJ. SCC* odstraní všechny uvozovky z řetězce "AuxPath".

- Řetězec "ProjName" v *MSSCCPRJ. Soubor SCC* se musí přesně shodovat s řetězcem vráceným z `SccGetProjPath` funkce. Pokud řetězec vrácený funkcí obsahuje uvozovky, řetězec v souboru *MSSCCPRJ. SCC* musí obsahovat uvozovky kolem tohoto a naopak.

- Soubor *MSSCCPRJ. SCC* se vytvoří nebo aktualizuje pokaždé, když je soubor umístěný pod správou zdrojových kódů.

- Pokud se soubor *MSSCCPRJ. SCC* odstraní, poskytovatel by ho měl znovu vygenerovat při příštím provedení operace správy zdrojových kódů týkající se tohoto adresáře.

- Soubor *MSSCCPRJ. SCC* musí přesně odpovídat definovanému formátu.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Ilustrace MSSCCPRJ Formát souboru SCC
 Následuje ukázka formátu souboru *MSSCCPRJ. SCC* (čísla řádků jsou k dispozici pouze jako vodítko a neměly by být součástí těla souboru):

- [Řádek 1] `SCC = This is a Source Code Control file`

- [Řádek 2]

- [Řádek 3] `[TestApp.sln]`

- [Řádek 4] `SCC_Aux_Path = "\\server\vss\"`

- [Řádek 5] `SCC_Project_Name = "$/TestApp"`

- [Řádek 6]

- [Řádek 7] `[TestApp.csproj]`

- [Řádek 8] `SCC_Aux_Path = "\\server\vss\"`

- [Řádek 9] `SCC_Project_Name = "$/TestApp"`

 První řádek uvádí účel souboru a slouží jako signatura pro všechny soubory tohoto typu. Tento řádek by měl vypadat přesně takto jako u všech souborů *MSSCCPRJ. SCC* :

 `SCC = This is a Source Code Control file`

 Následující část podrobně popisuje nastavení jednotlivých souborů označených názvem souboru v hranatých závorkách. Tato část se opakuje pro každý sledovaný soubor. Tento řádek je ukázkou názvu souboru, konkrétně `[TestApp.csproj]` . Rozhraní IDE očekává následující dva řádky. Ale nedefinuje styl definovaných hodnot. Proměnné jsou `SCC_Aux_Path` a `SCC_Project_Name` .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Do této části se nevztahují koncové oddělovače. Název souboru, stejně jako všechny literály, které se zobrazí v souboru, jsou definovány v souboru hlaviček SCC. h. Další informace naleznete v tématu [řetězce používané jako klíče pro vyhledání modulu plug-in správy zdrojového kódu](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).

## <a name="see-also"></a>Viz také
- [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)
- [Řetězce používané jako klíče pro vyhledání modulu plug-in správy zdrojového kódu](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
