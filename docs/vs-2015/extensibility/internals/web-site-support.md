---
title: Podpora webu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1a96504783de466551c6fb9d055b95ba38df760
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687693"
---
# <a name="web-site-support"></a>Podpora webu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Systém projektu webu je systém projektu, který vytváří webové projekty. Webové projekty v nástroji zase vytvářejí webové aplikace. Projekt webu generuje jeden spustitelný soubor pro každou webovou stránku, která má přidružený kód. Další spustitelné soubory jsou vygenerovány ze souborů zdrojového kódu ve složce/App_Code.  
  
 Systémy projektů webu jsou vytvořeny přidáním šablon a registračních atributů do stávajícího systému projektu. Jeden z těchto atributů vybírá poskytovatele technologie IntelliSense pro daný jazyk. Implementace poskytovatele technologie IntelliSense zpracovává odkazy a volá kompilátor jazyka, když je požadována inteligentní webová stránka, která není uložena v mezipaměti.  
  
 Kompilátor jazyka použitý ke kompilaci webových stránek musí být zaregistrován v [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] . Můžete použít [ \<compiler> prvek](https://msdn.microsoft.com/library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) v souboru Web.config k registraci kompilátoru, jako v následujícím příkladu:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Šablony podpory webu](../../extensibility/internals/web-site-support-templates.md)  
 Seznam šablon, které lze použít k vytvoření nových projektů webu a přidružených položek.  
  
 [Atributy podpory webu](../../extensibility/internals/web-site-support-attributes.md)  
 Prezentuje registrační atributy, které připojují webový projekt k [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] a [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] .  
  
## <a name="related-sections"></a>Související oddíly  
 [Webové projekty](../../extensibility/internals/web-projects.md)  
 Představuje přehled dvou druhů webových projektů, projektů webu a projektů webových aplikací.
