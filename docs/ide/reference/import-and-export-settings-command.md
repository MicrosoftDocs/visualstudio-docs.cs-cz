---
description: Importuje, exportuje nebo resetuje Visual Studio nastavení. Přípona souboru vssettings
title: nastavení importu a exportu – příkaz
ms.date: 05/28/2021
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dba50cf598c3c74f6c9407fbef5d55f938941a11
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687644"
---
# <a name="import-and-export-settings-command-vssettings-file"></a>Příkaz Import a export nastavení (soubor .vssettings)

Importuje, exportuje nebo resetuje Visual Studio souboru nastavení `.vssettings` .

Schéma souboru je otevřené. Nejčastěji se schéma řídí strukturou XML, kde každá kategorie je značka, která může sama obsahovat značky podkategorií. Tyto značky podkategorií mohou obsahovat značky hodnot vlastností. I když většina balíčků používá společnou strukturu, každý balíček v Visual Studio může do souboru přispívat libovolným kódem XML se schématem, které si zvolí.

## <a name="syntax"></a>Syntax

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>přepínače,

/export:`filename`

Nepovinný parametr. Exportuje aktuální nastavení do zadaného souboru.

/import:`filename`

Nepovinný parametr. Importuje nastavení v zadaném souboru.

/resetování

Nepovinný parametr. Obnoví aktuální nastavení.

## <a name="remarks"></a>Poznámky

Spuštěním tohoto příkazu bez přepínačů se **otevře průvodce importem a exportem nastavení.** Další informace najdete v tématu [Synchronizace nastavení a](../synchronized-settings-in-visual-studio.md) Nastavení [prostředí.](../environment-settings.md)

## <a name="example"></a>Příklad

Následující příkaz exportuje aktuální nastavení do souboru `MyFile.vssettings` :

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```



## <a name="see-also"></a>Viz také

- [Nastavení prostředí](../../ide/environment-settings.md)
- [Synchronizace nastavení](../../ide/synchronized-settings-in-visual-studio.md)
- [Přizpůsobení integrovaného vývojového Visual Studio (IDE)](../../ide/personalizing-the-visual-studio-ide.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
