---
title: Podpora webového serveru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d3da310c6695598eef36998cc562f6d477eff29
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139848"
---
# <a name="web-site-support"></a>Podpora webového serveru
Systém lokality webového projektu je systém projektu, který vytvoří webové projekty. Webové projekty zase vytvářet webové aplikace. Webový projekt generuje jeden spustitelný soubor pro každou webovou stránku, který je spojen kódu. Soubory zdrojového kódu ve složce /App_Code se generují další spustitelné soubory.  
  
 Projekt webové servery jsou vytvořené pomocí přidání šablony a atributy registrace do existujícího projektu systému. Jeden z těchto atributů vybere poskytovatele IntelliSense pro jazyk. Implementace zprostředkovatele IntelliSense zpracovává odkazy a volá kompilátor jazyka, pokud se požaduje inteligentní webové stránky, která není v mezipaměti.  
  
 Kompilátor jazyka, který používá ke kompilaci webové stránky musí být zaregistrovaný u [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. Můžete použít [ \<kompilátoru > Element](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) v souboru Web.config registrovat kompilátoru, jako v následujícím příkladu:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Šablony podpory webu](../../extensibility/internals/web-site-support-templates.md)  
 Seznam šablon, které můžete použít k vytvoření nové webové projekty a přidružené položky.  
  
 [Atributy podpory webu](../../extensibility/internals/web-site-support-attributes.md)  
 Představuje atributy registrace, které připojení webového projektu do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].  
  
## <a name="related-sections"></a>Související oddíly  
 [Webové projekty](../../extensibility/internals/web-projects.md)  
 Zobrazí přehled o dva druhy webové projekty – projekty webu a projekty webových aplikací.