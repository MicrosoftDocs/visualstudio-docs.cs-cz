---
title: '&lt;RelatedProducts – &gt; element (zaváděcí nástroj) | Microsoft Docs'
description: Element RelatedProducts definuje jiné produkty, které závisí buď na nebo jsou součástí aktuálního produktu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a7987306d9f7fc25f9f9b783d5b0966ac5015ce0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949685"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts – &gt; element (zaváděcí nástroj)
`RelatedProducts`Prvek definuje jiné produkty, které závisí buď na nebo jsou součástí aktuálního produktu.

## <a name="syntax"></a>Syntax

```xml
<RelatedProducts>
    <DependsOnProduct
        Code
    />
    <EitherProducts>
        <DependsOnProduct
            Code
        />
    </EitherProducts>
    <IncludesProduct
        Code
    />
</RelatedProducts>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `RelatedProducts`Prvek je podřízeným prvkem `Product` elementu. Nemá žádné atributy.

## <a name="dependsonproduct"></a>DependsOnProduct
 `DependsOnProduct`Prvek znamená, že aktuální produkt závisí na pojmenovaném produktu a že se má pojmenovaný produkt nainstalovat před aktuální. Je podřízeným `RelatedProducts` prvkem elementu. `RelatedProducts`Element může obsahovat jeden nebo více `DependsOnProduct` elementů.

 `DependsOnProduct` má následující atribut.

|Atribut|Popis|
|---------------|-----------------|
|`Code`|Název kódu zahrnutého produktu, jak je určeno `ProductCode` atributem `Product` elementu. Další informace naleznete v tématu [ \<Product> element](../deployment/product-element-bootstrapper.md).|

## <a name="eitherproducts"></a>EitherProducts
 `EitherProducts`Element definuje nula nebo více `DependsOnProduct` prvků a nemá žádné atributy. Alespoň jedna `DependsOnProduct` z těchto sad musí být nainstalována před aktuálním produktem. `RelatedProducts`Element může mít nula nebo více `EitherProducts` prvků.

## <a name="includesproduct"></a>IncludesProduct
 `IncludesProduct`Prvek znamená, že produkt je součástí aktuální instalace a nevyžaduje samostatnou instalaci. Je podřízeným `RelatedProducts` prvkem elementu. `RelatedProducts`Element může obsahovat jeden nebo více `IncludesProduct` elementů.

 `IncludesProduct` má následující atribut.

|Atribut|Popis|
|---------------|-----------------|
|`Code`|Název kódu zahrnutého produktu, jak je určeno `ProductCode` atributem `Product` elementu. Další informace naleznete v tématu [ \<Product> element](../deployment/product-element-bootstrapper.md).|

## <a name="example"></a>Příklad
 Následující příklad kódu určuje, že instalační služba společnosti Microsoft je nainstalovaná s .NET Framework, a proto nebude potřeba samostatnou instalaci.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>Viz také
- [\<Product> objekt](../deployment/product-element-bootstrapper.md)