---
title: Příkaz Nastavení importu a exportu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e3ee8549fd8cf1a4551818c013551ba24128f95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671055"
---
# <a name="import-and-export-settings-command"></a>Nastavení importu a exportu – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Import, export nebo obnovení [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nastavení.

## <a name="syntax"></a>Syntax

```
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Přepínače
 /export: `filename` volitelné. Exportuje aktuální nastavení do zadaného souboru.

 /Import: `filename` volitelné. Importuje nastavení v zadaném souboru.

 /Reset po vyčištění je nepovinný. Obnoví aktuální nastavení.

## <a name="remarks"></a>Poznámky
 Spuštění tohoto příkazu bez přepínačů otevře průvodce **importem a exportem nastavení** . Další informace najdete v tématu [Postup: sdílení nastavení mezi počítači nebo verzemi sady Visual Studio](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).

## <a name="example"></a>Příklad
 Následující příkaz exportuje nastavení aktuální do souboru `MyFile.vssettings` .

```
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Viz také
 [Přizpůsobení nastavení vývoje v](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [příkazech](../../ide/reference/visual-studio-commands.md) Visual Studio Visual Studio
