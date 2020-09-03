---
title: MSSCCPRJ. Soubor SCC | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 705e0fa821000716dc9cd729901fbb7db5fd759c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194214"
---
# <a name="mssccprjscc-file"></a>Soubor MSSCCPRJ.SCC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když je řešení sady Visual Studio nebo projekt umístěn pod správou zdrojových kódů pomocí rozhraní IDE, rozhraní IDE obdrží dvě klíčové informace z modulu plug-in správy zdrojových kódů ve formě řetězců. Tyto řetězce "AuxPath" a "ProjName" jsou neprůhledné na integrované vývojové prostředí (IDE), ale jsou používány modulem plug-in k vyhledání řešení nebo projektu ve správě verzí. Rozhraní IDE obvykle tyto řetězce obdrží při volání [SccGetProjPath](../extensibility/sccgetprojpath-function.md)a pak je uloží do souboru řešení nebo projektu pro budoucí volání [SccOpenProject](../extensibility/sccopenproject-function.md). Při vložení do souborů řešení a projektu se řetězce "AuxPath" a "ProjName" automaticky neaktualizují, pokud je uživatel větví, rozvětvení nebo kopíruje řešení a soubory projektu, které jsou ve správě verzí. Chcete-li zajistit, aby soubory řešení a projektu odkazovaly na správné místo v řízení verze, uživatelé musí ručně aktualizovat řetězce. Vzhledem k tomu, že jsou řetězce určeny jako neprůhledné, nemusí vždy být jasné, jak by se měly aktualizovat.  
  
 Modul plug-in správy zdrojových kódů se může vyhnout tomuto problému uložením řetězců "AuxPath" a "ProjName" do speciálního souboru s názvem MSSCCPRJ. Soubor SCC Jedná se o místní soubor na straně klienta, který je vlastněn a udržován modulem plug-in. Tento soubor není nikdy umístěn pod správou zdrojových kódů, ale je vygenerován modulem plug-in pro každý adresář, který obsahuje soubory se spravovanými zdroji. Aby bylo možné určit, které soubory jsou soubory řešení a projektu sady Visual Studio, modul plug-in správy zdrojových kódů může porovnat přípony souborů se standardním nebo uživatelem zadaným seznamem. Jakmile rozhraní IDE zjistí, že modul plug-in podporuje MSSCCPRJ. Soubor SCC, přestane vkládat řetězce "AuxPath" a "ProjName" do souborů řešení a projektu a čte tyto řetězce z MSSCCPRJ. Místo toho SCC soubor.  
  
 Modul plug-in správy zdrojového kódu, který podporuje MSSCCPRJ. Soubor SCC musí splňovat následující pokyny:  
  
- Může to být jenom jeden MSSCCPRJ. Soubor SCC na adresář.  
  
- MSSCCPRJ. Soubor SCC může obsahovat "AuxPath" a "ProjName" pro více souborů, které jsou pod správou zdrojových kódů v daném adresáři.  
  
- Řetězec "AuxPath" nesmí obsahovat v něm uvozovky. Může mít uvozovky kolem sebe jako oddělovače (například k označení prázdného řetězce lze použít dvojici dvojitých uvozovek). Rozhraní IDE bude při čtení z MSSCCPRJ z řetězce "AuxPath" oddělit všechny uvozovky. Soubor SCC  
  
- Řetězec "ProjName" v MSSCCPRJ. Soubor SCC se musí přesně shodovat s řetězcem vráceným z `SccGetProjPath` funkce. Pokud řetězec vrácený funkcí obsahuje uvozovky kolem tohoto řetězce, řetězec v MSSCCPRJ. Soubor SCC musí mít kolem sebe uvozovky a naopak.  
  
- MSSCCPRJ. Soubor SCC se vytvoří nebo aktualizuje pokaždé, když je soubor umístěný pod správou zdrojových kódů.  
  
- Pokud je MSSCCPRJ. Soubor SCC se odstraní, zprostředkovatel by ho měl znovu vygenerovat při příštím provedení operace správy zdrojových kódů týkající se tohoto adresáře.  
  
- MSSCCPRJ. Soubor SCC musí přesně odpovídat definovanému formátu.  
  
## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Ilustrace MSSCCPRJ Formát souboru SCC  
 Následuje ukázka MSSCCPRJ. Formát souboru SCC (čísla řádků se poskytují jenom jako vodítko a neměly by se zahrnovat do těla souboru):  
  
 [Řádek 1] `SCC = This is a Source Code Control file`  
  
 [Řádek 2]  
  
 [Řádek 3] `[TestApp.sln]`  
  
 [Řádek 4] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Řádek 5] `SCC_Project_Name = "$/TestApp"`  
  
 [Řádek 6]  
  
 [Řádek 7] `[TestApp.csproj]`  
  
 [Řádek 8] `SCC_Aux_Path = "\\server\vss\"`  
  
 [Řádek 9] `SCC_Project_Name = "$/TestApp"`  
  
 První řádek uvádí účel souboru a slouží jako signatura pro všechny soubory tohoto typu. Tento řádek by měl vypadat stejně jako ve všech MSSCCPRJ. Soubory SCC:  
  
 `SCC = This is a Source Code Control file`  
  
 Níže je uvedena část nastavení jednotlivých souborů označená názvem souboru v hranatých závorkách. Tato část se opakuje pro každý sledovaný soubor. Tento řádek je ukázkou názvu souboru, konkrétně `[TestApp.csproj]` . Rozhraní IDE očekává následující dva řádky. Ale nedefinuje styl definovaných hodnot. Proměnné jsou `SCC_Aux_Path` a `SCC_Project_Name` .  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Do této části se nevztahují koncové oddělovače. Název souboru, stejně jako všechny literály, které se zobrazí v souboru, jsou definovány v souboru hlaviček SCC. h. Další informace naleznete v tématu [řetězce používané jako klíče pro vyhledání modulu plug-in správy zdrojového kódu](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## <a name="see-also"></a>Viz také  
 [Moduly plug-in správy zdrojového kódu](../extensibility/source-control-plug-ins.md)   
 [Řetězce, které slouží jako klíče pro vyhledání modulu plug-in pro správu zdrojového kódu](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
