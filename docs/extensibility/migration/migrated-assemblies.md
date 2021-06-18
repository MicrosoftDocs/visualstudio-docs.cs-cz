---
title: Balíčky NuGet sady VS SDK
description: Přečtěte si o sadě VS SDK Metapackage a dalších balíčcích NuGet, které možná budete potřebovat při migraci rozšíření sady Visual Studio do sady Visual Studio 2022 Preview.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: dc55bd6abf2d5efabb862419e1bdd218d2ab18e7
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308691"
---
# <a name="sdk-reference-packages"></a>Balíčky odkazů sady SDK

[!INCLUDE [preview-note](../includes/preview-note.md)]

Nejjednodušší způsob, jak vytvořit rozšíření sady Visual Studio, je odkaz na [ `Microsoft.VisualStudio.Sdk` balíček NuGet](https://www.nuget.org/packages/microsoft.visualstudio.sdk).
Tento balíček je k dispozici pro cílení na Visual Studio 2017 (15,0), Visual Studio 2019 (16,0, 16,9) a nyní Visual Studio 2022.

V závislosti na vašem rozšíření může být potřeba přidat extra balíčky sady VS SDK, které nejsou zahrnuté do výše uvedeného meta balíčku.
Při odkazování na konkrétní jiné balíčky sady SDK se tyto balíčky můžou v různých verzích VS. lišit.

Všimněte si, že mnoho sestavení spolupráce bylo vloženo před Visual Studio 2022. Počínaje verzí Visual Studio 2022, vložení již není vyžadováno nebo není podporováno.
Místo propojení *použijte prosím naše* sestavení Interop.

Následující tabulka poskytuje mapování ze sestavení nebo balíčků, na které již může být rozšíření předsady Visual Studio 2022 odkazováno na nové ID balíčku, aby odkazovalo na cílení na Visual Studio 2022. V některých případech jsou sestavení nyní k dispozici v balíčcích NuGet, které byly dříve k dispozici pouze z místní instalace sady Visual Studio.

Předběžná verze sady Visual Studio 2022 | Visual Studio 2022
--|--
`envdte` | `Microsoft.VisualStudio.Interop`
`envdte100` | `Microsoft.VisualStudio.Interop`
`envdte80` | `Microsoft.VisualStudio.Interop`
`envdte90` | `Microsoft.VisualStudio.Interop`
`envdte90a` | `Microsoft.VisualStudio.Interop`
`extensibility` | `Microsoft.VisualStudio.Interop`
`Microsoft.MSXML` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.CommandBars` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Designer.Interfaces` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.OLE.Interop` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.SDK.EmbedInteropTypes` | Zastaralé. Odebrat odkaz.)
`Microsoft.VisualStudio.Shell.Embeddable` | `Microsoft.VisualStudio.Shell.Framework`
`Microsoft.VisualStudio.Shell.Interop.10.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.11.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.12.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.14.1.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.14.2.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.14.3.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.1.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.3.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.5.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.6.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.7.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.15.8.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.1.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.10.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.2.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.3.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.4.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.5.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.6.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.7.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.16.9.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.8.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop.9.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.Shell.Interop` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.10.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.11.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.12.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.12.1.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.14.2.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.15.0.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.15.1.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.16.0.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.8.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop.9.0` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.TextManager.Interop` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.UserNotifications.Interop.12.0.DesignTime` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.VSHelp.dll` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.VSHelp80.dll` | `Microsoft.VisualStudio.Interop`
`Microsoft.VisualStudio.WCFReference.Interop` | `Microsoft.VisualStudio.Interop`
`stdole` | `Microsoft.VisualStudio.Interop`
`VSLangProj` | `Microsoft.VisualStudio.Interop`
`VSLangProj100` | `Microsoft.VisualStudio.Interop`
`VSLangProj110` | `Microsoft.VisualStudio.Interop`
`VSLangProj140` | `Microsoft.VisualStudio.Interop`
`VSLangProj150` | `Microsoft.VisualStudio.Interop`
`VSLangProj157` | `Microsoft.VisualStudio.Interop`
`VSLangProj158` | `Microsoft.VisualStudio.Interop`
`VSLangProj165` | `Microsoft.VisualStudio.Interop`
`VSLangProj2` | `Microsoft.VisualStudio.Interop`
`VSLangProj80` | `Microsoft.VisualStudio.Interop`
`VSLangProj90` | `Microsoft.VisualStudio.Interop`

Všimněte si, kolik spolupracujících sestavení je teď dostupných jenom v jednom sloučeném definičním sestavení.
V případě, že se balíček v tabulce výše nezobrazuje, může být stejný v obou verzích.
