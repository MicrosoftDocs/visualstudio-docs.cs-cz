---
title: Registrace sloves pro přípony názvů souborů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac2854f1799075cc14d9beb557335be5228be21d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701536"
---
# <a name="register-verbs-for-file-name-extensions"></a>Registrace sloves pro přípony názvů souborů
Přidružení přípony názvu souboru s aplikací má obecně upřednostňovanou akci, ke které dochází, když uživatel poklepe na soubor. Tato upřednostňovaná akce je propojena se slovesem, například otevřeným, který odpovídá akci.

 Můžete zaregistrovat slovesa, která jsou přidružena k programovému identifikátoru (ProgID) pro rozšíření, pomocí klíče prostředí umístěného na **adrese HKEY_CLASSES_ROOT\{progid}\shell**. Další informace naleznete v [tématu Typy souborů](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Registrace standardních sloves
 Operační systém rozpozná následující standardní slovesa:

- Otevřít

- Upravit

- Hrát

- Tisk

- Preview

  Kdykoli je to možné, zaregistrujte standardní sloveso. Nejběžnější volbou je otevřené sloveso. Příkaz Upravit použijte pouze v případě, že existuje jasný rozdíl mezi otevřením souboru a úpravou souboru. Například otevření souboru *HTM* jej zobrazí v prohlížeči, zatímco úprava souboru *HTM* spustí editor HTML. Standardní slovesa jsou lokalizována s národním prostředím operačního systému.

> [!NOTE]
> Při registraci standardních sloves nenastavovat výchozí hodnotu pro klíč Otevřít. Výchozí hodnota obsahuje řetězec zobrazení v nabídce. Operační systém poskytuje tento řetězec pro standardní slovesa.

 Soubory projektu by měly být [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zaregistrovány, aby se spustila nová instance, kdy uživatel soubor otevře. Následující příklad ilustruje standardní registraci [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] slovesa pro projekt.

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 Chcete-li otevřít soubor v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]existující instanci aplikace , zaregistrujte klíč DDEEXEC. Následující příklad ilustruje standardní registraci [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] slovesa pro soubor *.cs.*

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>Nastavení výchozího slovesa
 Výchozí sloveso je akce, která se provede, když uživatel poklepe na soubor v Průzkumníkovi Windows. Výchozí sloveso je sloveso určené jako výchozí hodnota pro **HKEY_CLASSES_ROOT\\*progid*\Shell** klíč. Pokud není zadána žádná hodnota, je výchozí sloveso prvním slovesem zadaným v **\\HKEY_CLASSES_ROOT seznamu klíčů*progid*\Shell.**

> [!NOTE]
> Pokud plánujete změnit výchozí sloveso pro rozšíření v nasazení vedle sebe, zvažte dopad na instalaci a odebrání. Během instalace je původní výchozí hodnota přepsána.

## <a name="see-also"></a>Viz také
- [Správa přidružení souborů vedle sebe](../extensibility/managing-side-by-side-file-associations.md)
