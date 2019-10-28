---
title: Příkazy, které je třeba spustit po instalaci | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e85a03c71064687fdfbacf24b7aa59cd2a47f1a
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982026"
---
# <a name="commands-that-must-be-run-after-installation"></a>Příkazy, které se musí spustit po instalaci
Pokud nasadíte rozšíření prostřednictvím souboru *. msi* , je nutné spustit nástroj **devenv/Setup** jako součást instalace, aby aplikace Visual Studio mohla zjistit vaše rozšíření.

> [!NOTE]
> Informace v tomto tématu se vztahují na hledání souboru *devenv. exe* pomocí sady Visual Studio 2008 a starších verzí. Informace o tom, jak zjistit soubor *devenv. exe* s novějšími verzemi sady Visual Studio, najdete v tématu [zjištění systémových požadavků](../../extensibility/internals/detecting-system-requirements.md).

## <a name="find-devenvexe"></a>Najít devenv. exe
 Z hodnot registru, které [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalační programy pro zápis, můžete najít všechny verze nástroje *devenv. exe* , a to pomocí tabulky RegLocator a tabulek AppSearch k uložení hodnot registru jako vlastností. Další informace najdete v tématu [zjištění systémových požadavků](../../extensibility/internals/detecting-system-requirements.md).

### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator řádky tabulky pro vyhledání souboru devenv. exe z různých verzí sady Visual Studio

|Označení|Zobrazuje|Key|Name|Typ|
|-----------------|----------|---------|----------|----------|
|RL_DevenvExe_2002|odst|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|odst|
|RL_DevenvExe_2003|odst|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|odst|
|RL_DevenvExe_2005|odst|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|odst|
|RL_DevenvExe_2008|odst|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|odst|

### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Řádky tabulky AppSearch pro odpovídající řádky tabulky RegLocator

|Vlastnost|Označení|
|--------------|-----------------|
|DEVENV_EXE_2002|RL_DevenvExe_2002|
|DEVENV_EXE_2003|RL_DevenvExe_2003|
|DEVENV_EXE_2005|RL_DevenvExe_2005|
|DEVENV_EXE_2008|RL_DevenvExe_2008|

 Například instalační program sady Visual Studio zapíše hodnotu registru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS\EnvironmentPath** jako *C:\VS2008\Common7\IDE\devenv.exe*, úplnou cestu ke spustitelnému souboru je nutné spustit instalační program.

> [!NOTE]
> Vzhledem k tomu, že sloupec typu tabulka RegLocator je 2, není nutné zadávat další informace o verzi v tabulce podpisů.

## <a name="run-devenvexe"></a>Spustit devenv. exe
 Po spuštění standardní akce AppSearch v instalačním programu má každá vlastnost v tabulce AppSearch hodnotu, která odkazuje na soubor *devenv. exe* odpovídající verze sady Visual Studio. Pokud není k dispozici žádná z určených hodnot registru, protože tato verze sady Visual Studio není nainstalována – zadaná vlastnost je nastavena na hodnotu null.

 Instalační služba systému Windows podporuje spouštění spustitelného souboru, ke kterému vlastnost odkazuje prostřednictvím vlastního typu akce 50. Vlastní akce by měla zahrnovat možnosti spuštění skriptu `msidbCustomActionTypeInScript` (1024) a `msidbCustomActionTypeCommit` (512), aby bylo zajištěno, že rozhraní VSPackage bylo úspěšně nainstalováno před integrací do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Další informace najdete v tématu [CustomAction Table](/windows/desktop/msi/customaction-table) and [Custom Action Options in-Script Execution Options](/windows/desktop/msi/custom-action-in-script-execution-options).

 Vlastní akce typu 50 určují vlastnost obsahující spustitelný soubor jako hodnotu zdrojového sloupce a argumenty příkazového řádku v cílovém sloupci.

### <a name="customaction-table-rows-to-run-devenvexe"></a>Řádky tabulky CustomAction ke spuštění nástroje devenv. exe

|Akce|Typ|Zdroj|Cílové|
|------------|----------|------------|------------|
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|

 Vlastní akce musí být vytvořeny do tabulky InstallExecuteSequence, aby je bylo možné naplánovat na provedení při instalaci. V každém řádku sloupce podmínka použijte odpovídající vlastnost, abyste zabránili spuštění vlastní akce, pokud není v systému nainstalovaná verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

> [!NOTE]
> Vlastnosti s hodnotou null se vyhodnotí jako `False` při použití v podmínkách.

 Hodnota sloupce Sequence pro každou vlastní akci závisí na dalších hodnotách sekvence v balíčku Instalační služba systému Windows. Hodnoty sekvence by měly být takové, aby se vlastní akce nástroje *devenv. exe* spouštěly co nejblíže před standardní akcí volán InstallFinalize.

### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabulka InstallExecuteSequence k naplánování vlastních akcí nástroje devenv. exe

|Akce|Podmínka|Sequence|
|------------|---------------|--------------|
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|

## <a name="see-also"></a>Viz také:
- [Instalace VSPackage pomocí Instalační služba systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)