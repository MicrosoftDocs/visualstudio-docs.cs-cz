---
title: Atributy podpory webu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef75f99480145475278357a552f3ac74c0289800
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703502"
---
# <a name="web-site-support-attributes"></a>Atributy podpory webu
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Projekt webu lze rozšířit tak, aby poskytoval podporu pro webové programovací jazyky. Jazyk se musí [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zaregistrovat, aby se šablony projektu mohly zobrazit v dialogovém okně **Nový web,** když je jazyk vybrán.

Ukázka IronPython Studio obsahuje podporu webu. Ukázka obsahuje následující třídy atributů pro registraci IronPython jako kód za jazykem pro nové webové projekty.

## <a name="websiteprojectattribute"></a>Atribut websiteproject
 Tento atribut je umístěn v jazykovém projektu. Přidá jazyk do seznamu programovacích jazyků webu v seznamu **jazyk** v dialogovém okně **Nový web.** Například následující kód přidá IronPython do seznamu:

```
[WebSiteProject("IronPython", "Iron Python")]
public class PythonProjectPackage : ProjectPackage
```

 Tento atribut také nastaví cestu k šablonám tak, aby ukazovala na složku šablon. Další informace o umístění složky šablony naleznete v tématu [Šablony podpory webu](../../extensibility/internals/web-site-support-templates.md).

## <a name="websiteprojectrelatedfilesattribute"></a>Atribut WebSiteProjectRelatedFiles
 Tento atribut je umístěn v jazykovém projektu. Umožňuje projektu webu vnořit jeden typ souboru (související) pod jiný typ souboru (primární) v **Průzkumníku řešení**.

 Například následující kód určuje, že soubor kódu IronPython souvisí se souborem ASPX. Při vytvoření nové webové stránky ASPX v řešení webu IronPython je vygenerován nový zdrojový soubor .py a zobrazí se jako podřízený uzel stránky ASPX.

```
[WebSiteProjectRelatedFiles("aspx", "py")]
public class PythonProjectPackage : ProjectPackage
```

## <a name="provideintellisenseproviderattribute"></a>Atribut ProvideIntellisenseProviderAttribute
 Tento atribut je umístěn na balíčku jazykového projektu. Vybere poskytovatele technologie IntelliSense pro jazyk.

 Například následující kód určuje, že instance PythonIntellisenseProvider, <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>který implementuje , by měly být vytvořeny na vyžádání poskytovat jazykové služby.

```
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]
public class PythonPackage : Package, IOleComponent
```

 Implementace IVsIntellisenseProject zpracovává odkazy a volá kompilátor jazyka, když je požadována webová stránka s kódem, ale není uložena do mezipaměti.

## <a name="see-also"></a>Viz také
- [Podpora webu](../../extensibility/internals/web-site-support.md)
