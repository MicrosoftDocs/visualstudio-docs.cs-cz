---
title: Přispívání do dialogového okna Přidat novou položku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d288f2d007fd0f923021847179326069959d3698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197025"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Přispívání do dialogového okna Přidat novou položku
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtyp projektu může poskytnout kompletní nový adresář položek pro dialogové okno **Přidat novou položku** registrací šablon **Přidat položku** pod `Projects` podklíčem registru.  
  
## <a name="registering-add-new-item-templates"></a>Registrace šablon přidání nových položek  
 Tato část se nachází v části **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0\Projects** v registru. Níže uvedené položky registru předpokládají [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projekt agregovaný pomocí hypotetického podtypu projektu. Položky [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projektu jsou uvedeny níže.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 `AddItemTemplates\TemplateDirs`Podklíč obsahuje položky registru s cestou k adresáři, kde jsou umístěny položky k dispozici v dialogovém okně **Přidat novou položku** .  
  
 Prostředí automaticky načte všechna `AddItemTemplates` data do `Projects` podklíče registru. To může zahrnovat data pro implementace základního projektu a také data pro konkrétní typy podtypu projektu. Každý podtyp projektu je identifikován typem projektu `GUID` . Podtyp projektu může určit, že alternativní sada `Add Item` šablon by měla být použita pro konkrétní charakter instance projektu tím, že podporuje `VSHPROPID_ AddItemTemplatesGuid` výčet z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> v <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementaci pro návrat hodnoty identifikátoru GUID podtypu projektu. Není `VSHPROPID_AddItemTemplatesGuid` -li vlastnost zadána, je použit základní identifikátor GUID projektu.  
  
 Můžete filtrovat položky v dialogovém okně **Přidat novou položku** implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> rozhraní na objekt Agregátoru podtypu projektu. Například podtyp projektu, který implementuje projekt databáze agregací [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projektu, může filtrovat [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] konkrétní položky z dialogového okna **Přidat novou položku** pomocí implementace filtrování a pak může přidat položky konkrétního databázového projektu podporou `VSHPROPID_ AddItemTemplatesGuid` v <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Další informace o filtrování a přidávání položek do dialogového okna **Přidat novou položku** naleznete v tématu [Přidání položek do dialogových oken Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Identifikátory CATID pro objekty používané obvykle k rozšíření projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
