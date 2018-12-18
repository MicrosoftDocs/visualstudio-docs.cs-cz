---
title: Instalace sady Visual Studio SDK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 07/12/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c730edb6-5099-4c16-85a8-08def09f1455
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8dceab38f543c58997092559bf9a840806e9b013
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498584"
---
# <a name="install-the-visual-studio-sdk"></a>Instalace sady Visual Studio SDK

Visual Studio SDK (Software Development Kit) je volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později.  
  
## <a name="install-the-visual-studio-sdk-as-part-of-a-visual-studio-installation"></a>Instalace sady Visual Studio SDK jako součást instalace sady Visual Studio

Zahrnout VS SDK v instalaci sady Visual Studio, nainstalujte **vývoj rozšíření sady Visual Studio** úloha v části **další sady nástrojů**. Tato úloha nainstaluje Visual Studio SDK a nezbytné předpoklady. Instalace můžete dále ladit výběr nebo zrušení výběru součásti z **Souhrn** zobrazení.
  
## <a name="install-the-visual-studio-sdk-after-installing-visual-studio"></a>Instalace sady Visual Studio SDK po instalaci sady Visual Studio

Pokud chcete nainstalovat Visual Studio SDK po dokončení instalace sady Visual Studio, spusťte znovu instalační program sady Visual Studio a vyberte **vývoj rozšíření sady Visual Studio** pracovního vytížení.  
  
## <a name="install-the-visual-studio-sdk-from-a-solution"></a>Nainstalovat v rámci řešení sady Visual Studio SDK

Pokud otevřete řešení s projektem rozšíření bez první instalace VS SDK vás vyzve **nainstalovat chybějící funkce** dialogové okno k instalaci **vývoj rozšíření sady Visual Studio** úlohy:

![Vývoj rozšíření nainstalovat](../extensibility/media/install-extension-development.png "nainstalovat vývoj rozšíření")  
  
## <a name="install-the-visual-studio-sdk-from-the-command-line"></a>Instalace sady Visual Studio SDK z příkazového řádku

Jak pomocí sady Visual Studio úlohy nebo komponenty, můžete také nainstalovat **vývoj rozšíření sady Visual Studio** úloh (ID: Microsoft.VisualStudio.Workload.VisualStudioExtension) z příkazového řádku. Zobrazit [použít parametry příkazového řádku instalace sady Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) podrobné informace o přepínače příkazového řádku a obecné pokyny k určení úlohy nebo komponenty, identifikátory.
  
Všimněte si, že je nutné použít instalační program sady Visual Studio, který odpovídá vaší nainstalované verzi sady Visual Studio. Například pokud máte v počítači nainstalovaný Visual Studio Enterprise, musíte spustit instalační program sady Visual Studio Enterprise (*vs_enterprise.exe*).