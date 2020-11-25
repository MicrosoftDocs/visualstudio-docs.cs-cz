---
title: -ResetSettings (devenv.exe)
description: Naučte se, jak pomocí přepínače příkazového řádku devenv ResetSettings obnovit výchozí nastavení sady Visual Studio a automaticky spustit integrované vývojové prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 22b3308b3bd1fed6ff1bc3d1f3a5622eb6f8284f
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040027"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Obnoví výchozí nastavení sady Visual Studio a automaticky spustí integrované vývojové prostředí (IDE) sady Visual Studio. Tento přepínač volitelně obnoví nastavení na zadaný soubor nastavení.

Výchozí nastavení pochází z profilu, který byl vybrán při prvním spuštění aplikace Visual Studio.

> [!TIP]
> Informace o resetování nastavení pomocí integrovaného vývojového prostředí (IDE) najdete v tématu [resetování nastavení](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Syntaxe

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Argumenty

- *SettingsFile*

  Nepovinný parametr. Úplná cesta a název souboru s nastavením, které se mají použít pro sadu Visual Studio.

- *DefaultCollectionSpecifier*

  Nepovinný parametr. Specifikátor představující výchozí kolekci nastavení k obnovení. Vyberte jeden z výchozích specifikátorů kolekce uvedených v tabulce.

  | Název výchozí kolekce | Specifikátor kolekce |
  | --- | --- |
  | **Obecné** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Vizuál C #** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Vývoj webů** | `Web` |
  | **Vývoj pro web (jenom kód)** | `WebCode` |

## <a name="remarks"></a>Poznámky

Pokud není zadán žádný *SettingsFile* , IDE se otevře s existujícím nastavením.

## <a name="example"></a>Příklad

V prvním příkladu se aplikuje nastavení uložená v souboru `MySettings.vssettings` .

Druhý příklad obnoví výchozí profil Visual C#.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Viz také

- [Nastavení prostředí](../environment-settings.md)
- [Přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
