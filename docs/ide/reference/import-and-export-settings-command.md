---
description: Importuje, exportuje nebo resetuje nastavení sady Visual Studio.
title: nastavení importu a exportu – příkaz
ms.date: 11/21/2018
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
ms.openlocfilehash: 0f2ea4811af2c44277b9a6dc285972c5267b28d7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223667"
---
# <a name="import-and-export-settings-command"></a>nastavení importu a exportu – příkaz

Importuje, exportuje nebo resetuje nastavení sady Visual Studio.

## <a name="syntax"></a>Syntax

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>přepínače,

/Export`filename`

Nepovinný parametr. Exportuje aktuální nastavení do zadaného souboru.

/Import`filename`

Nepovinný parametr. Importuje nastavení v zadaném souboru.

/Reset po vyčištění

Nepovinný parametr. Obnoví aktuální nastavení.

## <a name="remarks"></a>Poznámky

Spuštění tohoto příkazu bez přepínačů otevře průvodce **importem a exportem nastavení** . Další informace najdete v tématu [synchronizace nastavení](../synchronized-settings-in-visual-studio.md) a [nastavení prostředí](../environment-settings.md).

## <a name="example"></a>Příklad

Následující příkaz exportuje aktuální nastavení do souboru `MyFile.vssettings` :

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Viz také

- [Nastavení prostředí](../../ide/environment-settings.md)
- [Synchronizovat nastavení](../../ide/synchronized-settings-in-visual-studio.md)
- [Přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
