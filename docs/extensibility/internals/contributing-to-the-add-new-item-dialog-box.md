---
title: Přispívání do dialogového okna Přidat novou položku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83444d9be6ba23392b792a0187bf46dc9920c465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709281"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Dialogové okno Přidat novou položku přispějte
Podtyp projektu může poskytnout úplný nový adresář položek pro dialogové okno **Přidat novou položku** registrací šablon **Přidat položku** pod podklíčem registru **Projekty.**

## <a name="register-add-new-item-templates"></a>Registrovat šablony nových položek
 Tato část je umístěna pod **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projekty** v registru. Níže uvedené položky [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registru předpokládají projekt agregovaný hypotetickým podtypem projektu. Položky projektu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jsou uvedeny níže.

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

 Podklíč **AddItemTemplates\TemplateDirs** obsahuje položky registru s cestou k adresáři, kde jsou umístěny položky zpřístupněné v dialogovém okně **Přidat novou položku.**

 Prostředí automaticky načte všechna data **AddItemTemplates** pod podklíčem registru **Projekty.** Tato data mohou zahrnovat data pro implementace základního projektu a také data pro konkrétní typy podtypů projektu. Každý podtyp projektu je identifikován identifikátorem **GUID**typu projektu . Podtyp projektu můžete určit, že alternativní sada **přidat šablony položky** by měla být `VSHPROPID_ AddItemTemplatesGuid` použita pro <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> konkrétní ochucené instance projektu podporou výčtu z v implementaci vrátit hodnotu GUID podtypu projektu. Pokud `VSHPROPID_AddItemTemplatesGuid` vlastnost není zadána, použije se identifikátor GUID základního projektu.

 Položky v dialogovém okně **Přidat novou položku** můžete filtrovat implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> rozhraní v objektu agregátoru podtypu projektu. Například podtyp projektu, který implementuje databázový projekt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] agregací [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu, může filtrovat určité položky z dialogového okna **Přidat novou položku** implementací filtrování a zase můžete přidat položky specifické pro databázi podporou `VSHPROPID_ AddItemTemplatesGuid` v <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Další informace o filtrování a přidávání položek do dialogového okna **Přidat novou položku** naleznete v [tématu Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATID pro objekty, které se obvykle používají k rozšíření projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
