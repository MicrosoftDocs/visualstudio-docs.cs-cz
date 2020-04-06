---
title: Instalace sady Visual Studio SDK | Dokumenty společnosti Microsoft
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f391708abbd8a9b66f2dfd5aaa6559cb075910d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710350"
---
# <a name="install-the-visual-studio-sdk"></a>Instalace sady Visual Studio SDK

Sada Visual Studio SDK (Software Development Kit) je volitelná funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalace sady Visual Studio SDK jako součást instalace sady Visual Studio

Chcete-li zahrnout sadu VS SDK do instalace sady Visual Studio, nainstalujte **úlohu vývoje rozšíření sady Visual Studio** v části Jiné sady **nástrojů**. Tato úloha nainstaluje sady Visual Studio SDK a nezbytné předpoklady. Instalaci můžete dále vyladit výběrem nebo zrušením výběru součástí ze **souhrnného** zobrazení.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalace sady Visual Studio SDK po instalaci sady Visual Studio

Chcete-li nainstalovat sadu Visual Studio SDK po dokončení instalace sady Visual Studio, spusťte znovu instalační program sady Visual Studio a vyberte **úlohu vývoje rozšíření sady Visual Studio.**

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Instalace sady Visual Studio SDK z řešení

Pokud otevřete řešení s projektem rozšiřitelnosti bez předchozí instalace sady VS SDK, budete vyzváni pomocí dialogového okna **Nainstalovat chybějící funkce** k instalaci **úlohy vývoje rozšíření sady Visual Studio:**

![Instalace vývoje rozšíření](../extensibility/media/install-extension-development.png "Instalace vývoje rozšíření")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Instalace sady Visual Studio SDK z příkazového řádku

Stejně jako u všech úloh nebo komponent sady Visual Studio můžete z příkazového řádku nainstalovat **také úlohu vývoje rozšíření sady Visual Studio** (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension). Podrobnosti o příslušných přepínačích příkazového řádku a obecné pokyny k určení identifikátorů pracovního vytížení nebo součásti naleznete v tématu [Použití parametrů příkazového řádku k instalaci sady Visual Studio.](../install/use-command-line-parameters-to-install-visual-studio.md)

Všimněte si, že je nutné použít instalační program sady Visual Studio, který odpovídá nainstalované verzi sady Visual Studio. Máte-li například v počítači nainstalovanou aplikaci Visual Studio Enterprise, je nutné spustit instalační program sady Visual Studio Enterprise (*vs_enterprise.exe*).
