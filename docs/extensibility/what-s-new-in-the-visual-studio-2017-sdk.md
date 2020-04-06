---
title: Co&#39;s novinkou ve Visual Studiu 2017 SDK | Dokumenty společnosti Microsoft
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88330aa68f2a3752431fd2fbe6c5c1c649acbb8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697197"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Co&#39;s novinkou v sadě Visual Studio 2017 SDK

Sada Visual Studio SDK obsahuje následující nové a aktualizované funkce pro Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formát VSIX v3

Pro podporu nové lehké instalace Visual Studia 2017 byl formát manifestu rozšíření VSIX aktualizován na verzi 3 (VSIX v3).

Nový formát podporuje:

* Explicitně deklarovat předpoklady, které mají být detekovány a nainstalovány VSIXInstaller.
* Ngen sestavy na rozšíření instalace.
* Instalace datových zdrojů mimo obvyklý kořen rozšíření.

Další informace o těchto změnách naleznete v následujících tématech:

* [Změny rozšiřitelnosti pro Visual Studio 2017](breaking-changes-2017.md)
* [Podpora Ngen ve VSIX v. 3](ngen-support.md)
* [Instalace mimo složku rozšíření](set-install-root.md)
* [Nejčastější dotazy týkající se rozšiřitelnosti sady Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrace projektu rozšiřitelnosti do Visual Studia 2017

Informace o tom, jak aktualizovat projekty rozšiřitelnosti a jejich manifesty VSIX do Visual Studia 2017, najdete v tématu [Jak: Migrace projektů rozšiřitelnosti do Sady Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Vlastní šablony projektů a položek

Počínaje Visual Studio 2017, hledání vlastních šablon projektů a položek již nebude provedeno. Místo toho rozšíření musí poskytnout soubory manifestu šablony, které popisují umístění instalace těchto šablon. Pomocí Visual Studia 2017 můžete aktualizovat rozšíření VSIX. Pokud nasadíte rozšíření pomocí MSI, musíte vygenerovat soubory manifestu šablony ručně. Další informace najdete [v tématu Upgrade vlastní chod projektů a šablon položek pro Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schéma manifestu šablony je popsáno v odkazu na schéma [manifestu šablony sady Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Aktualizované pokyny pro výkon rozšíření

K dispozici je nový [Postup: Diagnostikovat rozšíření výkonu](how-to-diagnose-extension-performance.md) článku v části [Spravovat VSPackages](managing-vspackages.md) ukázat, jak zjistit a analyzovat rozšíření dopad na spuštění sady Visual Studio a časy načítání řešení.
