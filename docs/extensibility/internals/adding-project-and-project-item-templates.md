---
title: Přidání šablon položek projektu a projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14eb1a9e2e63fa6e63d3ba2efa4426421e6b5593
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710199"
---
# <a name="add-project-and-project-item-templates"></a>Přidání šablon položek projektu a projektu
Při vytváření vlastních typů projektů je nutné poskytnout podporu pro přidávání [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nových projektů a položek projektu pomocí standardních dialogových oken integrovaného vývojového prostředí (IDE). Následující témata popisují různé techniky pro přidávání projektů a položek projektu.

## <a name="in-this-section"></a>V tomto oddílu
- [Kontext projektu](../../extensibility/internals/project-context.md)

 Vysvětluje, že projekt poskytuje většinu kontextové informace o tom, co se stane v prostředí.

- [Priorita projektu](../../extensibility/internals/project-priority.md)

 Vysvětluje, že položka projektu je obvykle členem jednoho projektu, aby se zabránilo nejednoznačnosti o tom, který projekt se používá k otevření položky.

- [Projekt různé soubory](../../extensibility/internals/miscellaneous-files-project.md)

 Obsahuje informace o dvou typech editorů, které lze použít k otevření souborů v projektu, a o roli, kterou projekt hraje při určování editoru, který se má použít při otevření položky projektu.

- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)

 Vysvětluje, co se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stane při vytvoření projektu.

- [Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Vysvětluje proces přidávání položek do dialogového okna **Přidat novou položku.**

- [Přidání adresářů do dialogového okna Nový projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Obsahuje příklad registrace nového adresáře, který obsahuje vlastní šablony zpřístupněné balíčkem VSPackage.

- [Přidání adresářů do dialogového okna Přidat novou položku](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Uvádí příklad registrace nové sady adresářů pro dialogové okno **Přidat novou položku.**

- [Příkazy definované ide pro rozšíření projektových systémů](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Uvádí různé typy položek příkazů používaných pro rozšíření projektových systémů.

- [CATID pro objekty, které se obvykle používají k rozšíření projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Seznam catidů pro objekty, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]které [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] se používají k rozšíření , a projektové systémy.

## <a name="related-sections"></a>Související oddíly
- [Postup: Otevření editorů specifických pro projekt](../../extensibility/how-to-open-project-specific-editors.md)

 Obsahuje podrobné pokyny pro otevření položky vnitřně vázané na konkrétní editor pro projekt.

- [Postup: Otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)

 Obsahuje podrobné pokyny pro otevření standardního editoru.

- [Podtypy projektu](../../extensibility/internals/project-subtypes.md)

 Obsahuje odkazy na koncepční témata podtypu projektu. Podtypy projektu [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] rozšiřují [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] stávající a projekty.

- [Typy projektů](../../extensibility/internals/project-types.md)

 Obsahuje odkazy na další témata, která nabízejí informace o tom, jak navrhnout nové typy projektů.
