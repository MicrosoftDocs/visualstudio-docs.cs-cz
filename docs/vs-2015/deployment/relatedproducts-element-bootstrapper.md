---
title: '&lt;RelatedProducts – &gt; element (zaváděcí nástroj) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70afe724be5b782bc90e162fd65f83ad1b0d0d23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202535"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts – &gt; element (zaváděcí nástroj)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`RelatedProducts`Prvek definuje jiné produkty, které závisí buď na nebo jsou součástí aktuálního produktu.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 Následující příklad kódu určuje, že instalační služba společnosti Microsoft je nainstalována s nástrojem [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , a proto nebude potřebovat samostatnou instalaci.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Viz také  
 [\<Product> Objekt](../deployment/product-element-bootstrapper.md)
