---
title: Příkazy, které je třeba spustit po instalaci | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- post-install commands
ms.assetid: c9601f2e-2c6e-4da9-9a6e-e707319b39e2
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 158119759f8e90161e1f3b5267be498dfc1c9b38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825188"
---
# <a name="commands-that-must-be-run-after-installation"></a>Příkazy, které se musí spustit po instalaci
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pokud nasadíte rozšíření prostřednictvím souboru. msi, je nutné spustit `devenv /setup` jako součást instalace, aby aplikace Visual Studio mohla zjistit vaše rozšíření.  
  
> [!NOTE]
> Informace v tomto tématu se vztahují na hledání DevEnv pomocí sady Visual Studio 2008 a starších verzí. Informace o tom, jak zjistit DevEnv s novějšími verzemi sady Visual Studio, najdete v tématu [zjištění systémových požadavků](../../extensibility/internals/detecting-system-requirements.md).  
  
## <a name="finding-devenvexe"></a>Hledání devenv.exe  
 Z hodnot registru, které [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] instalační programy zapisuje, můžete najít devenv.exe všech verzí, a to pomocí tabulky RegLocator a tabulky AppSearch ukládat hodnoty registru jako vlastnosti. Další informace najdete v tématu [zjištění systémových požadavků](../../extensibility/internals/detecting-system-requirements.md).  
  
### <a name="reglocator-table-rows-to-locate-devenvexe-from-different-versions-of-visual-studio"></a>RegLocator řádky tabulky k vyhledání devenv.exe z různých verzí sady Visual Studio  
  
|Signature_|Kořenová složka|Klíč|Název|Typ|  
|-----------------|----------|---------|----------|----------|  
|RL_DevenvExe_2002|2|SOFTWARE\Microsoft\VisualStudio\7.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2003|2|SOFTWARE\Microsoft\VisualStudio\7.1\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2005|2|SOFTWARE\Microsoft\VisualStudio\8.0\Setup\VS|EnvironmentPath|2|  
|RL_DevenvExe_2008|2|SOFTWARE\Microsoft\VisualStudio\9.0\Setup\VS|EnvironmentPath|2|  
  
### <a name="appsearch-table-rows-for-corresponding-reglocator-table-rows"></a>Řádky tabulky AppSearch pro odpovídající řádky tabulky RegLocator  
  
|Vlastnost|Signature_|  
|--------------|-----------------|  
|DEVENV_EXE_2002|RL_DevenvExe_2002|  
|DEVENV_EXE_2003|RL_DevenvExe_2003|  
|DEVENV_EXE_2005|RL_DevenvExe_2005|  
|DEVENV_EXE_2008|RL_DevenvExe_2008|  
  
 Například instalační program sady Visual Studio zapíše hodnotu registru **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\9.0\setup\vs\environmentpath** jako **C:\VS2008\Common7\IDE\devenv.exe**, úplná cesta ke spustitelnému souboru, který musí instalační program spustit.  
  
 **Poznámka:** Vzhledem k tomu, že sloupec typu RegLocator je 2, není nutné zadávat další informace o verzi v tabulce podpisů.  
  
## <a name="running-devenvexe"></a>Spuštění devenv.exe  
 Po spuštění standardní akce AppSearch v instalačním programu má každá vlastnost v tabulce AppSearch hodnotu odkazující na soubor devenv.exe pro odpovídající verzi sady Visual Studio. Pokud není k dispozici žádná z určených hodnot registru, protože tato verze sady Visual Studio není nainstalována – zadaná vlastnost je nastavena na hodnotu null.  
  
 Instalační služba systému Windows podporuje spouštění spustitelného souboru, ke kterému vlastnost odkazuje prostřednictvím vlastního typu akce 50. Vlastní akce by měla zahrnovat možnosti spuštění skriptu msidbCustomActionTypeInScript (1024) a msidbCustomActionTypeCommit (512), aby bylo zajištěno, že rozhraní VSPackage bylo úspěšně nainstalováno před integrací do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Další informace najdete v tématu CustomAction Table and Custom Action Options in-Script Execution Options.  
  
 Vlastní akce typu 50 určují vlastnost obsahující spustitelný soubor jako hodnotu zdrojového sloupce a argumenty příkazového řádku v cílovém sloupci.  
  
### <a name="customaction-table-rows-to-run-devenvexe"></a>CustomAction řádky tabulky, které se mají spustit devenv.exe  
  
|Akce|Typ|Zdroj|Cíl|  
|------------|----------|------------|------------|  
|CA_RunDevenv2002|1586|DEVENV_EXE_2002|/Setup|  
|CA_RunDevenv2003|1586|DEVENV_EXE_2003|/Setup|  
|CA_RunDevenv2005|1586|DEVENV_EXE_2005|/Setup|  
|CA_RunDevenv2008|1586|DEVENV_EXE_2008|/Setup|  
  
 Vlastní akce musí být vytvořeny do tabulky InstallExecuteSequence, aby je bylo možné naplánovat na provedení při instalaci. V každém řádku sloupce podmínka použijte odpovídající vlastnost, abyste zabránili spuštění vlastní akce, pokud tato verze nástroje není [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] v systému nainstalovaná.  
  
> [!NOTE]
> `Null` vlastnosti jsou vyhodnoceny jako `False` při použití v podmínkách.  
  
 Hodnota sloupce Sequence pro každou vlastní akci závisí na dalších hodnotách sekvence v balíčku Instalační služba systému Windows. Hodnoty sekvence by měly být takové, aby se devenv.exe vlastní akce spouštěly co nejblíže před standardní akcí volán InstallFinalize.  
  
### <a name="installexecutesequence-table-to-schedule-the-devenvexe-custom-actions"></a>Tabulka InstallExecuteSequence k naplánování vlastních akcí devenv.exe  
  
|Akce|Stav|Sequence|  
|------------|---------------|--------------|  
|CA_RunDevenv2002|DEVENV_EXE_2002|6602|  
|CA_RunDevenv2003|DEVENV_EXE_2003|6603|  
|CA_RunDevenv2005|DEVENV_EXE_2005|6605|  
|CA_RunDevenv2008|DEVENV_EXE_2008|6608|  
  
## <a name="see-also"></a>Viz také  
 [Instalace balíčků VSPackage pomocí Instalační služby systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
