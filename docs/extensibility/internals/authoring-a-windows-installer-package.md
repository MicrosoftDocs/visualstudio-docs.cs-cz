---
title: Vytváření balíčku Instalační služba systému Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa967b5f23ff9f4e5afa67b9b1cb4e83707616c6
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982232"
---
# <a name="author-a-windows-installer-package"></a>Vytvořit balíček Instalační služba systému Windows
Datové jednotky Instalační služba systému Windows modelu. Místo psaní skriptu procedurálního kopírování souborů a zápis položek registru například můžete vytvářet řádky a sloupce v databázových tabulkách, které obsahují data souborů a registru.

## <a name="database-entries"></a>Databázové položky
Chcete-li nainstalovat VSPackage, balíček Instalační služba systému Windows musí obsahovat databázové položky, aby bylo možné provádět následující úlohy:

- Vyhledejte v systému, jestli chcete najít verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vaše VSPackage podporuje (pomocí Instalační služba systému Windows tabulek, které zahrnují AppSearch, CompLocator, RegLocator, DrLocator a Signature).

- Zrušíte instalaci, pokud není nainstalovaná žádná podporovaná verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nebo pokud není splněn jiný požadavek na systém pro VSPackage (pomocí tabulky LaunchCondition).

- Nainstalujte rozhraní VSPackage a závislé soubory (pomocí adresáře, komponenty a tabulek souborů).

- Přidejte do registru vhodné informace pro VSPackage (pomocí tabulky registru).

- Integrujte VSPackage v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] voláním souboru **devenv. exe/setup** (pomocí tabulky CustomAction).

Další informace najdete v tématu [Instalační služba systému Windows](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Nástroje pro instalaci
Nejrůznější nástroje pro instalaci třetích stran poskytují vývojové prostředí pro Instalační služba systému Windows balíčky. K dispozici jsou tyto bezplatné nástroje:

- InstallShield – omezená edice

   Pomocí dialogového okna **Nový projekt** sady Visual Studio můžete získat omezené verze programu InstallShield. Rozbalte **jiné typy projektů** a potom vyberte **nastavení a nasazení**. Vyberte šablonu InstallShield.

- Sada nástrojů XML Instalační služba systému Windows

   Sada nástrojů Instalační služba systému Windows XML (WiX) vytváří Instalační služba systému Windows balíčky ze zdrojových souborů XML. Sada nástrojů WiX je projekt Microsoft Open-Source. Zdrojový kód a spustitelné soubory si můžete stáhnout ze sady [nástrojů WIX](https://sourceforge.net/projects/wix/).

   Komerční produkty, které se integrují do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pomocí [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], najdete v tématu [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Viz také:
- [Instalace VSPackage pomocí Instalační služba systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)