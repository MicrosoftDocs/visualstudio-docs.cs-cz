---
title: -ResetSettings (devenv.exe)
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
ms.openlocfilehash: eebcf2c6796723e51c3aefdb12575aa89779429f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593860"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Obnoví výchozí nastavení sady Visual Studio a automaticky spustí ide sady Visual Studio. Tento přepínač volitelně obnoví nastavení na zadaný soubor nastavení.

Výchozí nastavení pochází z profilu, který byl vybrán při prvním spuštění sady Visual Studio.

> [!TIP]
> Informace o tom, jak obnovit nastavení pomocí integrovaného vývojového prostředí (IDE), naleznete v [tématu Obnovení nastavení](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Syntaxe

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Argumenty

- *SettingsFile*

  Nepovinný parametr. Úplná cesta a název souboru nastavení, který se má použít pro visual studio.

- *DefaultCollectionSpecifier*

  Nepovinný parametr. Specifikátor představující výchozí kolekci nastavení k obnovení. Zvolte jeden z výchozích specifikátorů kolekce uvedených v tabulce.

  | Výchozí název kolekce | Specifikátor kolekce |
  | --- | --- |
  | **Obecné** | `General` |
  | **Javascript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Vizuální C #** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Vývoj webových aplikací** | `Web` |
  | **Vývoj webu (pouze kód)** | `WebCode` |

## <a name="remarks"></a>Poznámky

Pokud není zadán žádný *Soubor Nastavení,* ide se otevře pomocí existujícího nastavení.

## <a name="example"></a>Příklad

První příklad použije nastavení uložená `MySettings.vssettings`v souboru .

Druhý příklad obnoví výchozí profil Visual C#.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Viz také

- [Nastavení prostředí](../environment-settings.md)
- [Přizpůsobení prostředí IDE sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Devenv – přepínače příkazového řádku](../../ide/reference/devenv-command-line-switches.md)
