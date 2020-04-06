---
title: Vytvoření balíčku Instalační služby systému Windows | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d30c0e2b3b375e6e0efedddd3a017fbfb8646a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710028"
---
# <a name="author-a-windows-installer-package"></a>Vytvoření balíčku Instalační služby systému Windows
Data řídí model Instalační služby systému Windows. Místo psaní procedurálního skriptu pro kopírování souborů a zápis položek registru například vdatabázových tabulkách, které obsahují data souborů a registru, vytvoříte řádky a sloupce.

## <a name="database-entries"></a>Položky databáze
Chcete-li nainstalovat balíček VSPackage, musí balíček Instalační služby systému Windows obsahovat položky databáze, aby bylo nutné provádět následující úkoly:

- Vyhledejte v systému verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podpory Služby VSPackage (pomocí tabulek Instalační služby systému Windows, které obsahují aplikace AppSearch, CompLocator, RegLocator, DrLocator a Signature).

- Zrušte instalaci, pokud [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] není nainstalována žádná podporovaná verze programu Nebo pokud není splněn jiný systémový požadavek balíčku VSPackage (pomocí tabulky LaunchCondition).

- Nainstalujte soubory VSPackage a závislé soubory (pomocí tabulky adresářů, komponent a souborů).

- Přidejte příslušné informace pro VSPackage do registru (pomocí tabulky Registru).

- Integrujte VSPackage v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **voláním devenv.exe /setup** (pomocí tabulky CustomAction).

Další informace naleznete v [instalační službě systému Windows](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Nástroje pro nastavení
Různé nástroje pro nastavení jiných výrobců poskytují vývojové prostředí pro balíčky Instalační služby systému Windows. K dispozici jsou následující bezplatné nástroje:

- Limitovaná edice InstallShield

   Omezenou verzi programu InstallShield můžete získat prostřednictvím dialogového okna **Nový projekt** sady Visual Studio. Rozbalte **další typy projektů** a vyberte nastavení a **nasazení**. Vyberte šablonu InstallShield.

- Sada nástrojů XML Instalační služby systému Windows

   Sada nástrojů WiX (Installer XML) systému Windows vytváří balíčky Instalační služby systému Windows ze zdrojových souborů XML. Sada nástrojů WiX je projekt s otevřeným zdrojovým kódem společnosti Microsoft. Můžete si stáhnout zdrojový kód a spustitelné soubory z [sady nástrojů Wix](https://sourceforge.net/projects/wix/).

   Komerční produkty, které [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]integrují pomocí webu , naleznete v tématu [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Viz také
- [Instalace balíčků VSPackages s Instalační službou systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
