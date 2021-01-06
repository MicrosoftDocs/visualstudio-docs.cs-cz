---
title: Co &apos; je nového v sadě Visual Studio 2017 SDK | Microsoft Docs
description: Sada Visual Studio SDK má nové a aktualizované funkce pro sadu Visual Studio 2017, včetně aktualizovaného formátu VSIX verze 3.
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 79e9df9a728ab9892694efa6489a8ea1fd675700
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877624"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Co&#39;s novinkou v sadě Visual Studio 2017 SDK

Sada Visual Studio SDK obsahuje následující nové a aktualizované funkce pro sadu Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formát VSIX V3

Pro podporu nové instalace sady Visual Studio 2017 s nejnižší váhou se aktualizoval formát manifestu rozšíření VSIX na verzi 3 (VSIX V3).

Nový formát má podporu pro:

* Explicitní deklarace požadavků, které se mají detekovat a instalovat pomocí VSIXInstaller.
* Sestavení Ngen při instalaci rozšíření
* Instalace prostředků mimo obvyklý kořen rozšíření.

Další informace o těchto změnách najdete v následujících tématech:

* [Změny rozšiřitelnosti pro Visual Studio 2017](breaking-changes-2017.md)
* [Podpora Ngen ve VSIX v. 3](ngen-support.md)
* [Instalace mimo složku rozšíření](set-install-root.md)
* [Nejčastější dotazy k rozšiřitelnosti sady Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrovat projekt rozšiřitelnosti do sady Visual Studio 2017

Informace o tom, jak aktualizovat projekty rozšíření a jejich manifesty VSIX na Visual Studio 2017, naleznete v tématu [How to: migruje rozšiřující projekty do sady Visual studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Vlastní šablony projektů a položek

Počínaje verzí sady Visual Studio 2017 již nebude vyhledávání vlastních šablon projektů a položek provedeno. Místo toho musí rozšíření poskytnout soubory manifestu šablony, které popisují umístění instalace těchto šablon. Pomocí sady Visual Studio 2017 můžete aktualizovat rozšíření VSIX. Pokud nasadíte rozšíření pomocí MSI, je nutné vygenerovat soubory manifestu šablony ručně. Další informace najdete v tématu [Upgrade vlastních šablon projektů a položek pro Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schéma manifestu šablony je dokumentováno v [referenčních informacích o schématu manifestu šablony sady Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Aktualizované pokyny k výkonu rozšíření

K dispozici je nový [Postup: Diagnostika článku o výkonu rozšíření](how-to-diagnose-extension-performance.md) v části [Správa sady VSPackage](managing-vspackages.md) , která ukazuje, jak detekovat a analyzovat dopad rozšíření při spuštění sady Visual Studio a dobu načítání řešení.
