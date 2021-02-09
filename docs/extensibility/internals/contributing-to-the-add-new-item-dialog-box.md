---
title: Přispívání do dialogového okna Přidat novou položku | Microsoft Docs
description: Naučte se, jak přispívat do dialogového okna Přidat novou položku v aplikaci Visual Studio registrací šablon přidat položku v podklíči registru Projects.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e3fdc5705cad0ec696a520350042d7f18aaec146
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884634"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Přispívat do dialogového okna Přidat novou položku
Podtyp projektu může poskytnout kompletní nový adresář položek pro dialogové okno **Přidat novou položku** registrací šablon **Přidat položku** v podklíči registru **projekty** .

## <a name="register-add-new-item-templates"></a>Registrovat přidat nové položky šablony
 Tato část je umístěná v části **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** v registru. Níže uvedené položky registru předpokládají [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projekt agregovaný pomocí hypotetického podtypu projektu. Položky [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu jsou uvedeny níže.

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

 Podklíč **AddItemTemplates\TemplateDirs** obsahuje položky registru s cestou k adresáři, kde jsou umístěny položky, které byly k dispozici v dialogovém okně **Přidat novou položku** .

 Prostředí automaticky načte všechna **AddItemTemplates** data do podklíče registru **Projects** . Tato data mohou zahrnovat data pro implementace základního projektu i data pro konkrétní typy podtypu projektu. Každý podtyp projektu je identifikovaný **identifikátorem GUID** typu projektu. Podtyp projektu může určit, že alternativní Sada šablon pro **Přidání položek** by měla být použita pro konkrétní typ instance projektu tím, že podporuje `VSHPROPID_ AddItemTemplatesGuid` výčet z <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> v <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementaci a vrátí hodnotu identifikátoru GUID podtypu projektu. Není `VSHPROPID_AddItemTemplatesGuid` -li vlastnost zadána, je použit základní identifikátor GUID projektu.

 Můžete filtrovat položky v dialogovém okně **Přidat novou položku** implementací <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> rozhraní na objekt Agregátoru podtypu projektu. Například podtyp projektu, který implementuje projekt databáze agregací [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projektu, může filtrovat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] konkrétní položky z dialogového okna **Přidat novou položku** implementací filtrování a pak může přidat položky specifické pro projekt databáze podporou `VSHPROPID_ AddItemTemplatesGuid` v <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Další informace o filtrování a přidávání položek do dialogového okna **Přidat novou položku** naleznete v tématu [Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATID pro objekty, které se obvykle používají pro rozšiřování projektů](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
