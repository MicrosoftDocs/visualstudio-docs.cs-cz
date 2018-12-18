---
title: Přidání projektu a šablony položek projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: db53ddce3161097347760026aea16a51f8098519
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499631"
---
# <a name="add-project-and-project-item-templates"></a>Přidat projekt a šablony položek projektu
Když vytvoříte vlastní typy projektů, musíte poskytovat podporu pro přidání nové projekty a položky projektu pomocí standardní [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE) dialogových oknech. Následující témata popisují různé techniky pro přidání projektů a položek projektů.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Kontext projektu](../../extensibility/internals/project-context.md)  
 Tento článek vysvětluje, že projekt obsahuje většinu kontextové informace pro co ukáže v prostředí.  
  
 [Priorita projektu](../../extensibility/internals/project-priority.md)  
 Tento článek vysvětluje, že položka projektu je obvykle členem skupiny jednoho projektu, která pomáhá zabránit nejednoznačnost o tom, které se používá projekt, otevřete položku.  
  
 [Různé soubory projektu](../../extensibility/internals/miscellaneous-files-project.md)  
 Poskytuje informace o dva typy editorů, které lze použít k otevření souborů v projektu a roli hraje projektu při určování, které editor pro použití při otevření položky projektu.  
  
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)  
 Vysvětluje, co se stane, když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vytvoření projektu.  
  
 [Přidání položek do dialogových oken přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)  
 Vysvětluje postup přidání položky, které chcete **přidat novou položku** dialogové okno.  
  
 [Přidat adresářů do dialogového okna Nový projekt pole](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)  
 Poskytuje příklad registrace nového adresáře, který obsahuje vlastní šablony, které jsou k dispozici společností VSPackage.  
  
 [Přidat adresářů do dialogového okna Přidat novou položku](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)  
 Poskytuje příklad novou sadu adresářů pro registraci **přidat novou položku** dialogové okno.  
  
 [Příkazy definované prostředím IDE pro rozšíření systémů projektů](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)  
 Obsahuje seznam různých typů položek příkaz používá pro rozšíření systémů projektů.  
  
 [Identifikátory CatID pro objekty, které se obvykle používají k rozšíření projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)  
 Uvádí identifikátory CatID pro objekty, které se používají k rozšíření [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] systémy projektů.  
  
## <a name="related-sections"></a>Související oddíly  
 [Postupy: otevření editoru pro konkrétní projekt](../../extensibility/how-to-open-project-specific-editors.md)  
 Obsahuje podrobné pokyny pro otevírání položky vnitřně vázaný na zvláštní editor pro projekt.  
  
 [Postupy: otevření standardních editorů](../../extensibility/how-to-open-standard-editors.md)  
 Obsahuje podrobné pokyny pro otevření standardní editor.  
  
 [Podtypy projektů](../../extensibility/internals/project-subtypes.md)  
 Obsahuje odkazy na koncepční témata podtyp projektu. Podtypy projektů rozšířit existující [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] a [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projekty.  
  
 [Typy projektů](../../extensibility/internals/project-types.md)  
 Obsahuje odkazy na další témata, která nabízí informace o navrhování nových typů projektů.