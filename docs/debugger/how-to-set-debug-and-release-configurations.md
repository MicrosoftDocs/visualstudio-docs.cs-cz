---
title: Nastavení ladění a vydání konfigurace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/05/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a65a3331c210bdfb4143ff890180fdc7d663229
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257222"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Nastavení ladění a vydání konfigurace v sadě Visual Studio

Projekty aplikace Visual Studio mají samostatné verze a ladění konfigurace pro váš program. Vytváření verzí ladění pro ladění a verze vydání pro konečnou distribuci vydání.

V konfiguraci ladění váš program zkompiluje se sestaví neoptimalizovaná a obsahující symbolické ladicí informace. Optimalizace komplikuje ladění, protože vztah mezi zdrojovým kódem a vytvořenými pokyny je složitější.

Konfigurace programu pro vydání neobsahuje symbolické ladicí informace a je plně optimalizována. Ladit informace mohou být generovány v souborech PDB [v závislosti na možnostech kompilátoru](#BKMK_symbols_release) , která se používají. Vytváření souborů PDB může být užitečné, pokud budete muset později ladit vydané verze.

Další informace o konfiguracích sestavení naleznete v tématu [pochopení konfigurace sestavení](../ide/understanding-build-configurations.md).

Můžete změnit konfiguraci sestavení z **sestavení** nabídky, z panelu nástrojů nebo na stránkách vlastností projektu. Stránky vlastností projektu jsou specifické pro jazyk. Následující postup ukazuje, jak změnit konfiguraci sestavení z nabídky a panelu nástrojů. Další informace o tom, jak změnit konfiguraci sestavení v projektech v jiných jazycích najdete v článku [viz také](#see-also) níže v části.

## <a name="change-the-build-configuration"></a>Změňte konfiguraci buildu

Chcete-li změnit konfiguraci sestavení, buď:

* Z **sestavení** nabídce vyberte možnost **nástroje Configuration Manager**a pak vyberte **ladění** nebo **vydání**.

or

* Na panelu nástrojů zvolte buď **ladění** nebo **vydání** z **konfigurace řešení** seznamu.

  ![panely nástrojů sestavení konfigurace](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="BKMK_symbols_release"></a>Generovat soubory symbolů (PDB) pro sestavení (C#, C++, Visual Basic, F#)

Můžete také generovat soubory symbolů (PDB) a co ladit informace, včetně. Pro většinu typů projektu kompilátor generuje soubory symbolů ve výchozím nastavení pro ladění a verze sestavení, zatímco ostatní výchozí nastavení se liší podle typu projektu a verzi sady Visual Studio.

> [!IMPORTANT]
> Ladicí program načte pouze soubor PDB pro spustitelný soubor, který přesně odpovídá souboru .pdb vytvořeném, když byl sestaven spustitelný soubor (to znamená, že PDB musí být originál nebo kopie původního souboru .pdb). Další informace najdete v tématu [proč sada Visual Studio vyžaduje soubory symbolů ladicího programu shodovaly binárním souborům, se kterými byly vytvořeny?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

Každý typ projektu může mít jiný způsob nastavení těchto možností.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generovat soubory symbolů pro projekt C#, ASP.NET nebo Visual Basic

Podrobné informace o nastavení projektu pro konfiguraci ladění v jazyce C# nebo Visual Basic najdete v tématu [konfiguraci Ladit nastavení projektu pro jazyk C#](../debugger/project-settings-for-csharp-debug-configurations.md) nebo [nastavení projektu pro Visual Basic ladění konfigurace](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. V Průzkumníku řešení vyberte projekt.

2. Vyberte **vlastnosti** ikonu (nebo stiskněte klávesu **Alt + Enter**).

3. V podokně úloh zvolit **sestavení** (nebo **kompilaci** v jazyce Visual Basic).

4. V **konfigurace** klikněte na položku **ladění** nebo **vydání**.

5. Vyberte **Upřesnit** tlačítko (nebo **Upřesnit možnosti kompilace** tlačítko v jazyce Visual Basic).

6. V **ladicí informace** seznamu (nebo **Generovat ladicí informace** seznamu v jazyce Visual Basic), zvolte **úplné**, **pouze soubor Pdb**, nebo **Přenosné**.

   Přenosný formát je nejnovější formát pro různé platformy pro .NET Core. Další informace o možnostech najdete v tématu [dialogové okno Upřesnit nastavení sestavení (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Generování souborů PDB pro sestavení v jazyce C#](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Sestavte projekt.

   Kompilátor vytvoří soubory symbolů ve stejné složce jako spustitelný soubor nebo hlavního výstupního souboru.

### <a name="generate-symbol-files-for-a-c-project"></a>Generovat soubory symbolů pro projekt jazyka C++

1. V Průzkumníku řešení vyberte projekt.

2. Vyberte **vlastnosti** ikonu (nebo stiskněte klávesu **Alt + Enter**).

3. V **konfigurace** klikněte na položku **ladění** nebo **vydání**.

4. V podokně úloh zvolit **Linkeru > ladění**, vyberte možnosti pro **Generovat ladicí informace**.

   Podrobné informace o nastavení projektu pro konfiguraci ladění v jazyce C++, naleznete v tématu [konfiguraci Ladit nastavení projektu pro C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Konfigurace možností **generování souborů databáze programu**.

   Ve většině projektů C++, výchozí hodnota je `$(OutDir)$(TargetName).pdb`, který generuje soubory PDB do výstupní složky.

   ![Generování souborů PDB pro sestavení v jazyce C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Sestavte projekt.

   Kompilátor vytvoří soubory symbolů ve stejné složce jako spustitelný soubor nebo hlavního výstupního souboru.

## <a name="see-also"></a>Viz také
 
[Zadejte soubory symbolů (PDB) a zdrojových souborů v ladicím programu sady Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
[Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)<br/>
[Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
[Nastavení projektu pro konfiguraci ladění jazyka C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
[Nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
[Postupy: vytvoření a úprava konfigurací](../ide/how-to-create-and-edit-configurations.md)
