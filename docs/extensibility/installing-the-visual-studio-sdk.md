---
title: Instalace sady Visual Studio SDK | Microsoft Docs
description: Přečtěte si o možnostech instalace sady Visual Studio Software Development Kit, včetně při instalaci sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: overview
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 331a219210c990aed2f9601cd1f9b1f0bc5710ed
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079160"
---
# <a name="install-the-visual-studio-sdk"></a>Instalace sady Visual Studio SDK

Sada Visual Studio SDK (Software Development Kit) je volitelná funkce instalačního programu sady Visual Studio. Sadu VS SDK můžete také nainstalovat později.

## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalace sady Visual Studio SDK jako součást instalace sady Visual Studio

Pokud chcete v instalaci sady Visual Studio zahrnout sadu VS SDK, nainstalujte do **jiných sad nástrojů** úlohu **vývoj rozšíření sady Visual Studio** . Tato úloha nainstaluje sadu Visual Studio SDK a nezbytné požadavky. Instalaci můžete dále vyladit tak, že vyberete nebo zrušíte výběr komponent ze **souhrnného** zobrazení.

## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Nainstalovat sadu Visual Studio SDK po instalaci sady Visual Studio

Chcete-li po dokončení instalace sady Visual Studio nainstalovat sadu Visual Studio SDK, spusťte znovu instalační program sady Visual Studio a vyberte úlohu **vývoj rozšíření sady Visual Studio** .

## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Instalace sady Visual Studio SDK z řešení

Pokud otevřete řešení s projektem rozšiřitelnosti bez první instalace sady VS SDK, zobrazí se dialogové okno **instalace chybějící funkce** pro instalaci úlohy **vývoje rozšíření sady Visual Studio** :

![Nainstalovat vývoj rozšíření](../extensibility/media/install-extension-development.png "Nainstalovat vývoj rozšíření")

## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Instalace sady Visual Studio SDK z příkazového řádku

Stejně jako u libovolné úlohy nebo součásti sady Visual Studio můžete také nainstalovat úlohu **vývoj rozšíření sady Visual Studio** (ID: Microsoft. VisualStudio. reVisualStudioExtension) z příkazového řádku. Podrobnosti o příslušných přepínačích příkazového řádku a obecných pokynech k určení zátěžových identifikátorů a jejich součástí najdete v tématu [použití parametrů příkazového řádku k instalaci sady Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) .

Všimněte si, že je nutné použít instalační program sady Visual Studio, který odpovídá nainstalované verzi sady Visual Studio. Například pokud máte v počítači nainstalovanou Visual Studio Enterprise, musíte spustit instalační program Visual Studio Enterprise (*vs_enterprise.exe*).
