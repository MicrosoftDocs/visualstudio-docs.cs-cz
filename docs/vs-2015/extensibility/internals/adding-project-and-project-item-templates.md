---
title: Přidávání šablon projektů a položek projektů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b68c9f4bbaed73603c46fc0beab77a308b8933d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203856"
---
# <a name="adding-project-and-project-item-templates"></a>Přidávání šablon projektů a položek projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Při vytváření vlastních typů projektů je nutné poskytnout podporu pro přidávání nových projektů a položek projektu pomocí standardních dialogových [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] oken integrované vývojové prostředí (IDE). Následující témata popisují různé techniky pro přidávání projektů a položek projektu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Kontext projektu](../../extensibility/internals/project-context.md)  
 Vysvětluje, že projekt poskytuje většinu kontextových informací o tom, co se v prostředí zobrazuje.  
  
 [Priorita projektu](../../extensibility/internals/project-priority.md)  
 Vysvětluje, že položka projektu je obvykle členem jednoho projektu, aby se zabránilo nejednoznačnému způsobu, jakým je projekt použit k otevření položky.  
  
 [Projekt Ostatní soubory](../../extensibility/internals/miscellaneous-files-project.md)  
 Poskytuje informace o dvou typech editorů, které lze použít k otevření souborů v projektu a roli, kterou projekt hraje při určování editoru, který se použije při otevření položky projektu.  
  
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)  
 Vysvětluje, co se stane při [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Vytvoření projektu.  
  
 [Přidávání položek do dialogových oken Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Vysvětluje proces přidávání položek do dialogového okna **Přidat novou položku** .  
  
 [Přidávání adresářů do dialogového okna Nový projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Obsahuje příklad registrace nového adresáře, který obsahuje vlastní šablony, které zpřístupňuje VSPackage.  
  
 [Přidávání adresářů do dialogového okna Přidat novou položku](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 V této části najdete příklad registrace nové sady adresářů pro dialogové okno **Přidat novou položku** .  
  
 [Příkazy definované prostředím IDE pro rozšíření systémů projektů](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Uvádí různé typy položek příkazů, které se používají pro rozšiřování systémů projektů.  
  
 [Identifikátory CATID pro objekty používané obvykle k rozšíření projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Obsahuje seznam CATID pro objekty, které se používají k rozšiřování [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] , [!INCLUDE[csprcs](../../includes/csprcs-md.md)] a [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] systémům projektů.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: Otevření editoru pro konkrétní projekt](../../extensibility/how-to-open-project-specific-editors.md)  
 Poskytuje podrobné pokyny pro otevření položky vnitřně vázané na určitý editor pro projekt.  
  
 [Postupy: Otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)  
 Poskytuje podrobné pokyny pro otevření standardního editoru.  
  
 [Podtypy projektů](../../extensibility/internals/project-subtypes.md)  
 Obsahuje odkazy na koncepční témata podtypů projektu. Podtypy projektů rozšíří existující [!INCLUDE[csprcs](../../includes/csprcs-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projekty a.  
  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Obsahuje odkazy na další témata, která nabízejí informace o návrhu nových typů projektů.
