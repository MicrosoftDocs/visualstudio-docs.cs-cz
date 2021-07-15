---
title: co &apos; je nového v sadě Visual Studio 2017 SDK | Microsoft Docs
description: sada Visual Studio SDK obsahuje nové a aktualizované funkce pro Visual Studio 2017, včetně aktualizovaného formátu VSIX verze 3.
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0b0b7852fa7e20f4ee6951e57c5c19f4b5454028
ms.sourcegitcommit: 3c6c263a1c0b20f084290ce45295a46027da33b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/14/2021
ms.locfileid: "113756895"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>novinky v sadě Visual Studio 2017 SDK pro&#39;s

sada Visual Studio SDK obsahuje následující nové a aktualizované funkce pro Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formát VSIX V3

pro podporu nové instalace Visual Studio 2017 je formát manifestu rozšíření VSIX aktualizovaný na verzi 3 (VSIX v3).

Nový formát má podporu pro:

* Explicitní deklarace požadavků, které se mají detekovat a instalovat pomocí VSIXInstaller.
* Sestavení Ngen při instalaci rozšíření
* Instalace prostředků mimo obvyklý kořen rozšíření.

Další informace o těchto změnách najdete v následujících tématech:

* [změny rozšiřitelnosti pro Visual Studio 2017](breaking-changes-2017.md)
* [Podpora Ngen ve VSIX v. 3](ngen-support.md)
* [Instalace mimo složku rozšíření](set-install-root.md)
* [nejčastější dotazy k rozšíření Visual Studio 2017](faq-2017.yml)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>migrovat projekt rozšiřitelnosti na Visual Studio 2017

chcete-li zjistit, jak aktualizovat projekty rozšíření a jejich manifesty VSIX na Visual Studio 2017, přečtěte si téma [how to: migrace rozšiřujících projektů do Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Vlastní šablony projektů a položek

počínaje Visual Studio 2017 se již neprovádí vyhledávání vlastních šablon projektů a položek. Místo toho musí rozšíření poskytnout soubory manifestu šablony, které popisují umístění instalace těchto šablon. k aktualizaci rozšíření VSIX můžete použít Visual Studio 2017. Pokud nasadíte rozšíření pomocí MSI, je nutné vygenerovat soubory manifestu šablony ručně. další informace najdete v tématu [Upgrade vlastních šablon projektů a položek pro Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). schéma manifestu šablony je dokumentováno v [referenčních informacích o schématu manifestu Visual Studio šablony](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Aktualizované pokyny k výkonu rozšíření

k dispozici je nový [postup: diagnostika článku o výkonu rozšíření](how-to-diagnose-extension-performance.md) v části [správa sady vspackage](managing-vspackages.md) , která ukazuje, jak detekovat a analyzovat dopad rozšíření při Visual Studio spouštění a načítání řešení.
