---
title: Spravované třídy architektury balíčku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: 2e9fe1abb82d3d64232e3e5e2a6d117c1068aa1c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297700"
---
# <a name="managed-package-framework-classes"></a>Spravované třídy architektury balíčku
Třídy spravovaného balíčku (MPF) lze použít k vytvoření VSPackage pomocí spravovaného kódu. Poskytují výchozí implementace pro mnoho rozhraní VSPackage. Po skrytí podrobností a složitosti implementace vám umožňuje vytvořit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrační produkty s minimálním množstvím kódu.  
  
> [!WARNING]
> Většina sestavení, která obsahují spravované třídy balíčků architektury, je dodávána se sadou Visual Studio SDK. Můžete stáhnout zdrojový kód pro spravovanou zabalenou architekturu pro projekty ve [spravovaném rozhraní balíčku pro projekty](https://archive.codeplex.com/?p=mpfproj11).  
  
## <a name="mpf-namespaces"></a>MPF – obory názvů  
 V následující tabulce jsou uvedeny obory názvů MPF poskytované [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
|Obor názvů|Obsah|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Obsahuje užitečné třídy pro zpracování chyb COM, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] konstant a oken Win32.|  
|<xref:Microsoft.VisualStudio.Package>|Obsahuje obálku spravovaného kódu pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekty, editory a MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Zahrnuje MPF základní třídy, ze kterých můžete odvodit implementaci mnoha běžných objektů sady Visual Studio.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Obsahuje rozšíření návrháře [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Obsahuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření návrháře serializace.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Obsahuje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření CodeDom Designer.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Podporuje podtypy projektů (označují se také jako "charakter").|  
  
## <a name="see-also"></a>Viz také  
 [Sady VSPackage a  architektury spravovaného balíčku](../misc/vspackages-and-the-managed-package-framework.md)  
 [Pomocí sestavení spolupráce sady Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [Sady VSPackage a Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)