---
title: Přidání přepínačů příkazového řádku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f2df3a704c34d97c9d5acfa72249fe492b7f812
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740162"
---
# <a name="add-command-line-switches"></a>Přidání přepínačů příkazového řádku
Můžete přidat přepínače příkazového řádku, které se vztahují k vašemu balíčku VSPackage při spuštění *devenv.exe.* Slouží <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> k deklarování názvu přepínače a jeho vlastností. V tomto příkladu je přidán přepínač MySwitch pro podtřídu VSPackage s názvem **AddCommandSwitchPackage** bez argumentů a s vspackage načten automaticky.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 Pojmenované parametry jsou uvedeny v následujících popisech.

||||
|-|-|-|-|
| Parametr | Popis|
| Argumenty | Počet argumentů pro přepínač. Může být "*" nebo seznam argumentů. |
| Náklad poptávky | Načtěte VSPackage automaticky, pokud je nastavena na 1, jinak nastavena na 0. |
| Řetězec nápovědy | Řetězec nápovědy nebo ID prostředku řetězce, který se má zobrazit pomocí **devenv /?**. |
| Name (Název) | Vypínač. |
| BalíčekGuid | GUID balíčku. |

 První hodnota Arguments je obvykle 0 nebo 1. Zvláštní hodnotu '*' lze použít k označení, že celý zbytek příkazového řádku je argument. To může být užitečné pro ladění scénáře, kde uživatel musí předat v řetězci příkazu ladicího programu.

 Hodnota DemandLoad je `true` buď (1) nebo `false` (0) označuje, že VSPackage by měla být načtena automaticky.

 Hodnota HelpString je ID prostředku řetězce, který se zobrazí v **devenv /?** Nápověda k zobrazení. Tato hodnota by měla být ve tvaru "#nnn", kde nnn je celé číslo. Hodnota řetězce v souboru prostředků by měla končit novým znakem řádku.

 Název hodnota je název přepínače.

 PackageGuid hodnota je GUID balíčku, který implementuje tento přepínač. IDE používá tento identifikátor GUID k vyhledání balíčku VSPackage v registru, na který se vztahuje přepínač příkazového řádku.

## <a name="retrieve-command-line-switches"></a>Načtení přepínačů příkazového řádku
 Po načtení balíčku můžete přepínače příkazového řádku načíst provedením následujících kroků.

1. V <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementaci VSPackage volání `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> získat <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> rozhraní.

2. Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> k načtení přepínačů příkazového řádku, které uživatel zadal.

   Následující kód ukazuje, jak zjistit, zda byl přepínač příkazového řádku MySwitch zadán uživatelem:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 Je vaší odpovědností zkontrolovat přepínače příkazového řádku při každém načtení balíčku.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Devenv – přepínače příkazového řádku](../ide/reference/devenv-command-line-switches.md)
- [Nástroj CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. Pkgdef soubory](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
