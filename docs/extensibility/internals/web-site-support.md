---
title: Podpora webu | Microsoft Docs
description: Seznamte se se systémy projektů webu, které jsou vytvářeny přidáním šablon a registračních atributů do stávajícího systému projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 16de0fdc2c4e65dfe6c2ae2c6dc3cdc6902fa8b0
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069101"
---
# <a name="web-site-support"></a>Podpora webu
Systém projektu webu je systém projektu, který vytváří webové projekty. Webové projekty v nástroji zase vytvářejí webové aplikace. Projekt webu generuje jeden spustitelný soubor pro každou webovou stránku, která má přidružený kód. Další spustitelné soubory jsou vygenerovány ze souborů zdrojového kódu ve složce/App_Code.

 Systémy projektů webu jsou vytvořeny přidáním šablon a registračních atributů do stávajícího systému projektu. Jeden z těchto atributů vybírá poskytovatele technologie IntelliSense pro daný jazyk. Implementace poskytovatele technologie IntelliSense zpracovává odkazy a volá kompilátor jazyka, když je požadována inteligentní webová stránka, která není uložena v mezipaměti.

 Kompilátor jazyka použitý ke kompilaci webových stránek musí být zaregistrován v [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] . Můžete použít [ \<compiler> prvek](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element) v souboru Web.config k registraci kompilátoru, jako v následujícím příkladu:

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>V tomto oddílu
- [Šablony podpory webu](../../extensibility/internals/web-site-support-templates.md)

 Seznam šablon, které lze použít k vytvoření nových projektů webu a přidružených položek.

- [Atributy podpory webu](../../extensibility/internals/web-site-support-attributes.md)

 Prezentuje registrační atributy, které připojují webový projekt k [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)] .

## <a name="related-sections"></a>Související oddíly
- [Webové projekty](../../extensibility/internals/web-projects.md)

 Představuje přehled dvou druhů webových projektů, projektů webu a projektů webových aplikací.
