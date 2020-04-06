---
title: Příkazy, které musí být spuštěny po instalaci | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77add5afd5d44358f0077a11bb70559a796e74c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709476"
---
# <a name="commands-that-must-be-run-after-installation"></a>Příkazy, které musí být spuštěny po instalaci
Pokud nasadíte rozšíření prostřednictvím souboru *MSI,* je nutné spustit **devenv /setup** jako součást instalace, aby Visual Studio zjišťovalo vaše rozšíření.

> [!NOTE]
> Informace v tomto tématu platí pro hledání *devenv.exe* s Visual Studio 2008 a starší. Informace o tom, jak zjistit *devenv.exe* s novějšími verzemi sady Visual Studio, naleznete [v tématu Zjišťování systémových požadavků](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Najít devenv.exe
 Můžete vyhledat *devenv.exe* každé verze z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hodnot registru, které instalátory psát, pomocí Tabulky RegLocator a AppSearch tabulky pro uložení hodnoty registru jako vlastnosti. Další informace naleznete v [tématu Zjištění systémových požadavků](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>Řádky tabulky RegLocator pro vyhledání devenv.exe z různých verzí sady Visual Studio

|Podpis|Kořenová složka|Klíč|Name (Název)|Typ|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|Cesta prostředí|2|
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|Cesta prostředí|2|
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|Cesta prostředí|2|
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|Cesta prostředí|2|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Řádky tabulky AppSearch pro odpovídající řádky tabulky RegLocator

|Vlastnost|Podpis|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Instalační program sady Visual Studio například zapíše hodnotu registru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** jako *C:\VS2008\Common7\IDE\devenv.exe*, což je úplná cesta ke spustitelnému souboru, který musí instalační program spustit.

> [!NOTE]
> Vzhledem k tomu, že sloupec Typ tabulky RegLocator je 2, není nutné zadat další informace o verzi v tabulce Podpis.

## <a name="run-devenvexe"></a>Spustit devenv.exe
 Po spuštění standardní akce AppSearch v instalačním programu má každá vlastnost v tabulce AppSearch hodnotu ukazující na soubor *devenv.exe* pro odpovídající verzi sady Visual Studio. Pokud některá ze zadaných hodnot registru nejsou k dispozici , zadaná vlastnost je nastavena na hodnotu null.

 Instalační služba systému Windows podporuje spuštění spustitelného souboru, na který vlastnost odkazuje prostřednictvím vlastního typu akce 50. Vlastní akce by měla zahrnovat možnosti `msidbCustomActionTypeInScript` spuštění ve skriptu `msidbCustomActionTypeCommit` (1024) a (512), aby bylo zajištěno, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]že VSPackage byl úspěšně nainstalován před integrací do . Další informace naleznete v [tématu CustomAction table](/windows/desktop/msi/customaction-table) and [Custom action in-script execution options](/windows/desktop/msi/custom-action-in-script-execution-options).

 Vlastní akce typu 50 určují vlastnost obsahující spustitelný soubor jako hodnotu sloupce Zdroj a argumenty příkazového řádku ve sloupci Cíl.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Řádky tabulky CustomAction pro spuštění devenv.exe

|Akce|Typ|Zdroj|Cíl|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/nastavení|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/nastavení|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/nastavení|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/nastavení|

 Vlastní akce musí být vytvořeny do tabulky InstallExecuteSequence, aby byly během instalace spuštěny. Použijte odpovídající vlastnost v každém řádku sloupce Podmínka, abyste zabránili spuštění [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vlastní akce, pokud tato verze aplikace není v systému nainstalována.

> [!NOTE]
> Vlastnosti s hodnotou null jsou vyhodnoceny při `False` použití v podmínkách.

 Hodnota sloupce Sekvence pro každou vlastní akci závisí na dalších hodnotách sekvence v balíčku Instalační služby systému Windows. Hodnoty sekvence by měly být takové, aby vlastní akce *devenv.exe* běžely co nejblíže bezprostředně před standardní akcí InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabulka InstallExecuteSequence pro naplánování vlastních akcí devenv.exe

|Akce|Podmínka|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Viz také
- [Instalace balíčků VSPackages pomocí Instalační služby systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
