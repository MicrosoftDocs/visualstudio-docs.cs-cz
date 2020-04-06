---
title: MSSCCPRJ. Spis SCC | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89511b7c8b69c5793eceef7d58153dde253a4f47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702472"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Soubor SCC
Při umístění řešení sady Visual Studio nebo projektu pod smytí zdrojového kódu pomocí ide, ide obdrží dva klíčové informace. Informace pochází z modulu plug-in správy zdrojového kódu ve formě řetězců. Tyto řetězce" "AuxPath" a "ProjName", jsou neprůhledné pro IDE, ale jsou používány modulem plug-in k vyhledání řešení nebo projektu v řízení verzí. IDE obvykle získá tyto řetězce poprvé voláním [SccGetProjPath](../extensibility/sccgetprojpath-function.md)a potom uloží do souboru řešení nebo projektu pro budoucí volání [SccOpenProject](../extensibility/sccopenproject-function.md). Při vložení do souborů řešení a projektu řetězce "AuxPath" a "ProjName" nejsou automaticky aktualizovány, když uživatel větve, větve nebo kopie řešení a projektové soubory, které jsou ve správě verzí. Chcete-li se ujistit, že soubory řešení a projektu odkazují na jejich správné umístění ve správě verzí, musí uživatelé ručně aktualizovat řetězce. Vzhledem k tomu, že řetězce jsou určeny k neprůhledné, nemusí být vždy jasné, jak by měly být aktualizovány.

 Modul plug-in správy zdrojového kódu se může tomuto problému vyhnout uložením řetězců "AuxPath" a "ProjName" do speciálního souboru nazývaného soubor *MSSCCPRJ.SCC.* Jedná se o místní soubor na straně klienta, který je vlastněn a spravován modulem plug-in. Tento soubor není nikdy umístěn pod správou zdrojového kódu, ale je generován modulem plug-in pro každý adresář, který obsahuje soubory řízené zdrojem. Chcete-li zjistit, které soubory jsou soubory sady Visual Studio a soubory projektu, modul plug-in správy zdrojového kódu můžete porovnat přípony souborů proti standardní nebo uživatelem dodaný seznam. Jakmile ide zjistí, že modul plug-in podporuje soubor *MSSCCPRJ.SCC,* přestane vložit řetězce "AuxPath" a "ProjName" do souborů řešení a projektu a místo toho přečte tyto řetězce ze souboru *MSSCCPRJ.SCC.*

 Modul plug-in správy zdrojového kódu, který podporuje soubor *MSSCCPRJ.SCC,* musí dodržovat následující pokyny:

- V jednom adresáři může být pouze jeden soubor *MSSCCPRJ.SCC.*

- Soubor *MSSCCPRJ.SCC* může obsahovat "AuxPath" a "ProjName" pro více souborů, které jsou pod smyčkovou správou zdrojového kódu v daném adresáři.

- Řetězec "AuxPath" nesmí obsahovat uvozovky uvnitř. Je povoleno mít uvozovky kolem něj jako oddělovače (například pár dvojitých uvozovek lze použít k označení prázdný řetězec). IDE bude strip všechny citace z řetězce "AuxPath" při čtení ze souboru *MSSCCPRJ.SCC.*

- Řetězec "ProjName" v *MSSCCPRJ. Soubor SCC* musí přesně odpovídat `SccGetProjPath` řetězci vrácenému z funkce. Pokud řetězec vrácený funkcí obsahuje uvozovky kolem něj, řetězec v souboru *MSSCCPRJ.SCC* musí mít uvozovky kolem něj a naopak.

- Soubor *MSSCCPRJ.SCC* je vytvořen nebo aktualizován vždy, když je soubor umístěn pod shodou zdrojového kódu.

- Pokud soubor *MSSCCPRJ.SCC* odstraní, zprostředkovatel by měl znovu vygenerovat při příštím provedení operace správy zdrojového kódu týkající se tohoto adresáře.

- Soubor *MSSCCPRJ.SCC* musí přísně dodržovat definovaný formát.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Ilustrace MSSCCPRJ. Formát souboru SCC
 Následuje ukázka formátu souboru *MSSCCPRJ.SCC* (čísla řádků jsou uvedena pouze jako vodítko a neměla by být zahrnuta do těla souboru):

- [Řádek 1]`SCC = This is a Source Code Control file`

- [Řádek 2]

- [Řádek 3]`[TestApp.sln]`

- [Řádek 4]`SCC_Aux_Path = "\\server\vss\"`

- [Řádek 5]`SCC_Project_Name = "$/TestApp"`

- [Řádek 6]

- [Řádek 7]`[TestApp.csproj]`

- [Řádek 8]`SCC_Aux_Path = "\\server\vss\"`

- [Řádek 9]`SCC_Project_Name = "$/TestApp"`

 První řádek uvádí účel souboru a slouží jako podpis pro všechny soubory tohoto typu. Tento řádek by měl vypadat přesně takhle ve všech souborech *MSSCCPRJ.SCC:*

 `SCC = This is a Source Code Control file`

 Následující část podrobně popisuje nastavení pro každý soubor, označený názvem souboru v hranatých závorkách. Tato část se opakuje pro každý sledovaný soubor. Tento řádek je ukázkou názvu souboru, a to . `[TestApp.csproj]` Ide očekává následující dva řádky. Nedefinuje však styl definovaných hodnot. Proměnné jsou `SCC_Aux_Path` a `SCC_Project_Name`.

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 V této části neexistuje žádný koncový oddělovač. Název souboru a všechny literály, které se v souboru zobrazují, jsou definovány v hlavičkovém souboru scc.h. Další informace naleznete [v tématu Řetězce používané jako klíče pro hledání modulu plug-in správy zdrojového kódu](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).

## <a name="see-also"></a>Viz také
- [Moduly plug-in pro směřuje zdroj](../extensibility/source-control-plug-ins.md)
- [Řetězce používané jako klíče pro nalezení modulu plug-in správy zdrojového kódu](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
