---
title: Vytváření balíčku Instalační služba systému Windows | Microsoft Docs
description: Naučte se, jak vytvořit balíček Instalační služba systému Windows pro sadu Visual Studio, který se skládá z tabulek databáze obsahující data souborů a registru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: afc21237b72d76b73e619740cab0b196e29e928d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078952"
---
# <a name="author-a-windows-installer-package"></a>Vytvořit balíček Instalační služba systému Windows
Datové jednotky Instalační služba systému Windows modelu. Místo psaní skriptu procedurálního kopírování souborů a zápis položek registru například můžete vytvářet řádky a sloupce v databázových tabulkách, které obsahují data souborů a registru.

## <a name="database-entries"></a>Databázové položky
Chcete-li nainstalovat VSPackage, balíček Instalační služba systému Windows musí obsahovat databázové položky, aby bylo možné provádět následující úlohy:

- Vyhledejte v systému, kde najdete verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vaší sady VSPackage (pomocí Instalační služba systému Windows tabulek, které zahrnují AppSearch, CompLocator, RegLocator, DrLocator a Signature).

- Zrušíte instalaci, pokud není nainstalovaná žádná podporovaná verze nástroje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nebo pokud není splněn jiný požadavek na systém pro VSPackage (pomocí tabulky LaunchCondition).

- Nainstalujte rozhraní VSPackage a závislé soubory (pomocí adresáře, komponenty a tabulek souborů).

- Přidejte do registru vhodné informace pro VSPackage (pomocí tabulky registru).

- Integrujte VSPackage do v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] voláním **devenv.exe/Setup** (pomocí tabulky CustomAction).

Další informace najdete v tématu [Instalační služba systému Windows](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Nástroje pro instalaci
Nejrůznější nástroje pro instalaci třetích stran poskytují vývojové prostředí pro Instalační služba systému Windows balíčky. K dispozici jsou tyto bezplatné nástroje:

- InstallShield – omezená edice

   Pomocí dialogového okna **Nový projekt** sady Visual Studio můžete získat omezené verze programu InstallShield. Rozbalte **jiné typy projektů** a potom vyberte **nastavení a nasazení**. Vyberte šablonu InstallShield.

- Sada nástrojů XML Instalační služba systému Windows

   Sada nástrojů Instalační služba systému Windows XML (WiX) vytváří Instalační služba systému Windows balíčky ze zdrojových souborů XML. Sada nástrojů WiX je projekt Microsoft Open-Source. Zdrojový kód a spustitelné soubory si můžete stáhnout ze sady [nástrojů WIX](https://sourceforge.net/projects/wix/).

   U komerčních produktů, které se integrují do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pomocí [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , se podívejte na téma [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Viz také
- [Instalace VSPackage pomocí Instalační služba systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
