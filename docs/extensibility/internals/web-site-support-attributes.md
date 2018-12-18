---
title: Webové stránky podpory atributy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b312322c1d707f13c5121f1fd159f3fd7736886c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140833"
---
# <a name="web-site-support-attributes"></a>Atributy webu podpory
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Webový projekt lze rozšířit zajistit podporu pro webové programovacích jazyků. Jazyk musí se registrovat s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tak, aby šablony projektů může vyskytovat v **nový web** dialogové okno když je vybraný jazyk.

Ukázka IronPython Studio zahrnuje podporu webu. Ukázka obsahuje následující třídy atributů k registraci IronPython jako codebehind jazyk pro nové webové projekty.

## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute
 Tento atribut je umístěn na projekt jazyka. Jazyk ho přidá do seznamu webových programovacích jazyků v **jazyk** v seznamu **nový web** dialogové okno. Následující kód například přidá IronPython do seznamu:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Tento atribut nastaví také cestu šablony tak, aby odkazoval na složku šablony. Další informace o umístění složky šablony najdete v tématu [webu podpory šablony](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute
 Tento atribut je umístěn na projekt jazyka. Webový projekt lze vnořit jeden typ souboru (souvisejících) umožňuje v rámci jiného typu souboru (primární) v **Průzkumníku řešení**.

 Například následující kód určuje, že soubor codebehind IronPython vztahuje na soubor .aspx. Při vytvoření nové webové stránky .aspx v řešení lokality IronPython webové nový soubor .py zdroje se vygeneruje a zobrazí se jako podřízený uzel stránky .aspx.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute
 Tento atribut je umístěn na jazykovou sadu projektu. Vybere poskytovatele IntelliSense pro jazyk.

 Například následující kód určuje, že instance PythonIntellisenseProvider, která implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, by se měl vytvořit na vyžádání k poskytování služeb jazyk.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Implementace IVsIntellisenseProject zpracovává odkazy a volá kompilátor jazyka, pokud webové stránky s kódem je požadována, ale není v mezipaměti.

## <a name="see-also"></a>Viz také
 [Podpora webu](../../extensibility/internals/web-site-support.md)