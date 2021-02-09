---
title: Přidávání šablon projektů a položek projektů | Microsoft Docs
description: Přečtěte si o přidání projektů a šablon položek projektů do dialogových oken v integrovaném vývojovém prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ff54e24408577ba8bfbf553a5c641eab2d15814
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906234"
---
# <a name="add-project-and-project-item-templates"></a>Přidat šablony projektů a položek projektů
Při vytváření vlastních typů projektů je nutné poskytnout podporu pro přidávání nových projektů a položek projektu pomocí standardních dialogových [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oken integrované vývojové prostředí (IDE). Následující témata popisují různé techniky pro přidávání projektů a položek projektu.

## <a name="in-this-section"></a>V této části
- [Kontext projektu](../../extensibility/internals/project-context.md)

 Vysvětluje, že projekt poskytuje většinu kontextových informací o tom, co se v prostředí zobrazuje.

- [Priorita projektu](../../extensibility/internals/project-priority.md)

 Vysvětluje, že položka projektu je obvykle členem jednoho projektu, aby se zabránilo nejednoznačnému způsobu, jakým je projekt použit k otevření položky.

- [Projekt různých souborů](../../extensibility/internals/miscellaneous-files-project.md)

 Poskytuje informace o dvou typech editorů, které lze použít k otevření souborů v projektu a roli, kterou projekt hraje při určování editoru, který se použije při otevření položky projektu.

- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)

 Vysvětluje, co se stane při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Vytvoření projektu.

- [Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Vysvětluje proces přidávání položek do dialogového okna **Přidat novou položku** .

- [Přidání adresářů do dialogového okna Nový projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Obsahuje příklad registrace nového adresáře, který obsahuje vlastní šablony, které zpřístupňuje VSPackage.

- [Přidání adresářů do dialogového okna Přidat novou položku](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 V této části najdete příklad registrace nové sady adresářů pro dialogové okno **Přidat novou položku** .

- [Příkazy definované rozhraním IDE pro rozšíření systémů projektů](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Uvádí různé typy položek příkazů, které se používají pro rozšiřování systémů projektů.

- [CATID pro objekty, které se obvykle používají pro rozšiřování projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Obsahuje seznam CATID pro objekty, které se používají k rozšiřování [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] , [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] systémům projektů.

## <a name="related-sections"></a>Související oddíly
- [Postupy: otevření editorů specifických pro projekt](../../extensibility/how-to-open-project-specific-editors.md)

 Poskytuje podrobné pokyny pro otevření položky vnitřně vázané na určitý editor pro projekt.

- [Postupy: otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)

 Poskytuje podrobné pokyny pro otevření standardního editoru.

- [Podtypy projektu](../../extensibility/internals/project-subtypes.md)

 Obsahuje odkazy na koncepční témata podtypů projektu. Podtypy projektů rozšíří existující [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekty a.

- [Typy projektů](../../extensibility/internals/project-types.md)

 Obsahuje odkazy na další témata, která nabízejí informace o návrhu nových typů projektů.
