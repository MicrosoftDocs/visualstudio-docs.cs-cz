---
title: Podpora webových stránek | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 22047ad1b0709cefa200656e61f8e0d39ace94c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703446"
---
# <a name="web-site-support"></a>Podpora webu
Systém projektu webu je projektový systém, který vytváří webové projekty. Webové projekty zase vytvářejí webové aplikace. Webový projekt generuje jeden spustitelný soubor pro každou webovou stránku, která má přidružený kód. Další spustitelné soubory jsou generovány ze souborů zdrojového kódu ve složce /App_Code.

 Systémy projektu webu jsou vytvářeny přidáním šablon a atributů registrace do existujícího systému projektu. Jeden z těchto atributů vybere pro jazyk zprostředkovatele Technologie IntelliSense. Implementace zprostředkovatele Technologie IntelliSense zpracovává odkazy a volá kompilátor jazyka, když je požadována inteligentní webová stránka, která není uložena v mezipaměti.

 Kompilátor jazyka používaný ke kompilaci [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]webových stránek musí být registrován u aplikace . Kompilátor> Element v souboru Web.config můžete použít k registraci kompilátoru, jako v následujícím příkladu: [ \<](/dotnet/framework/configure-apps/file-schema/compiler/compiler-element)

```
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>
```

## <a name="in-this-section"></a>V tomto oddílu
- [Šablony podpory webu](../../extensibility/internals/web-site-support-templates.md)

 Zobrazí seznam šablon, které lze použít k vytvoření nových projektů webu a přidružených položek.

- [Atributy podpory webu](../../extensibility/internals/web-site-support-attributes.md)

 Představuje atributy registrace, které připojují projekt webu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].

## <a name="related-sections"></a>Související oddíly
- [Webové projekty](../../extensibility/internals/web-projects.md)

 Představuje přehled dvou druhů webových projektů, webových projektů a projektů webových aplikací.
