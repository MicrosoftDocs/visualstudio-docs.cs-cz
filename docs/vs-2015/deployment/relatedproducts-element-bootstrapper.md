---
title: '&lt;RelatedProducts&gt; – Element (zaváděcí nástroj) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: c78aa559bf64b110909134426c676f302ca5fe04
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49296293"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; – Element (zaváděcí nástroj)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`RelatedProducts` Element definuje jiné produkty, které závisí na nebo jsou součástí aktuální produkt.  
  
## <a name="syntax"></a>Syntaxe  
  
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
 `RelatedProducts` Element je podřízeným prvkem `Product` elementu. Nemá žádné atributy.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 `DependsOnProduct` Element označuje, že aktuální produkt závisí na uvedený produkt a, uvedený produkt by měla být nainstalována před aktuální. Je podřízeným prvkem `RelatedProducts` elementu. A `RelatedProducts` element může obsahovat jeden nebo více `DependsOnProduct` elementy.  
  
 `DependsOnProduct` má následující atribut.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Code`|Název kódu součástí produktu, jak jsou určené `ProductCode` atribut `Product` elementu. Další informace najdete v tématu [ \<produktu > Element](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 `EitherProducts` Element definuje nula nebo více `DependsOnProduct` elementy, a nemá žádné atributy. Alespoň jeden `DependsOnProduct` v této sadě musí být nainstalována před aktuální produkt. A `RelatedProducts` prvek může mít nula nebo více `EitherProducts` elementy.  
  
## <a name="includesproduct"></a>IncludesProduct  
 `IncludesProduct` Element označuje, že je obsažen v aktuální instalaci produktu a už nevyžadují samostatnou instalaci. Je podřízeným prvkem `RelatedProducts` elementu. A `RelatedProducts` element může obsahovat jeden nebo více `IncludesProduct` elementy.  
  
 `IncludesProduct` má následující atribut.  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Code`|Název kódu součástí produktu, jak jsou určené `ProductCode` atribut `Product` elementu. Další informace najdete v tématu [ \<produktu > Element](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu určuje, že je součástí Microsoft Installer [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]a proto nebudete potřebovat samostatné instalace.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Viz také  
 [\<Produkt > – Element](../deployment/product-element-bootstrapper.md)



