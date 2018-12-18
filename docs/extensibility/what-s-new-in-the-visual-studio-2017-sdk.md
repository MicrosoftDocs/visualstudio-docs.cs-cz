---
title: Co&#39;nového ve Visual Studio 2017 SDK | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/31/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6f2a003bc19764aa07262552d3f0cc41316835b6
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566905"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Co&#39;nového ve Visual Studio 2017 SDK

Visual Studio SDK obsahuje následující nové a aktualizované funkce pro Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formát VSIX v3

Pro podporu nové odlehčené instalace sady Visual Studio 2017, byla aktualizována na verzi 3 (VSIX v. 3) formát manifestu rozšíření VSIX.

Nový formát obsahuje podporu pro:

* Požadované součásti zjištěny a nainstalovat VSIXInstaller explicitní deklarace.
* Ngen sestavení na instalaci rozšíření.
* Instalace prostředky mimo kořenový obvykle rozšíření.

Další informace o těchto změnách, naleznete v následujících tématech:

* [Změny do rozšíření pro 2017](breaking-changes-2017.md)
* [Podpora Ngen ve VSIX v. 3](ngen-support.md)
* [Instalace mimo složku rozšíření](set-install-root.md)
* [Nejčastější dotazy pro rozšiřitelnost sady Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Migrovat projekt rozšíření sady Visual Studio 2017

Zjistěte, jak aktualizovat vaše rozšíření projektů a jejich manifestů VSIX do sady Visual Studio 2017, najdete v článku [postupy: migrace projektů rozšíření do sady Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Vlastní šablony projektů a položek

Spouští se v sadě Visual Studio 2017, vyhledávání vlastních projektů a šablon položek už se provede. Rozšíření místo toho musíte zadat soubory manifestu šablon, které popisují umístění instalace služby tyto šablony. Visual Studio 2017 můžete použít k aktualizaci rozšíření VSIX. Pokud provádíte nasazení vašeho rozšíření pomocí MSI, musíte soubory manifestu šablony vygenerovat ručně. Další informace najdete v tématu [Upgrade vlastních šablon projektů a položek pro Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schéma manifestu šablony je popsána v [odkaz na schéma manifestu šablon sady Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Pokyny k výkonu aktualizované rozšíření

Je tu nový [postupy: Diagnostika výkonu rozšíření](how-to-diagnose-extension-performance.md) článku v části [Správa balíčky VSPackages](managing-vspackages.md) ukazují, jak detekovat a analyzovat dopad rozšíření v sadě Visual Studio při spuštění a řešení zatížení časy.
