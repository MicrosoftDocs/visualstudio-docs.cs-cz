---
title: Bitmap – Element | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 624a8e4a47e7043c2e3726f23b9d2a94defdea32
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846652"
---
# <a name="bitmap-element"></a>Bitmap – element
Definuje rastrový obrázek. Rastrový obrázek je načten z prostředku nebo ze souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|identifikátor GUID|Požadováno. Identifikátor GUID identifikátoru GUID a ID příkazu.<br /><br /> Atribut guid rastrového obrázku není přidružené žádné VSPackage nebo jiné skupiny příkazů.  Musí být jedinečné pro definici bitmapy a neměl by se používat k žádnému jinému účelu.|  
|resID|ID identifikátoru GUID a ID příkazu. Je požadován resID nebo atribut href.<br /><br /> Atribut resID je ID prostředku celé číslo, které určuje pruhu rastrový obrázek, který má být načten při slučování tabulky příkazů.  Při načítání tabulky příkazů rastrové obrázky určené ID prostředku se načtou z prostředku stejného modulu.|  
|usedList|Povinné, pokud je přítomen atribut resID. Vybere dostupných imagí v pruhu rastrového obrázku.|  
|href|Cesta k rastrového obrázku. Je požadován resID nebo atribut href.<br /><br /> Cesty zahrnutí se hledá soubor uvedeného obrázku, který je součástí výsledný binární soubor.  Během sloučení příkaz tabulky zkopírovat bitovou kopii a je potřeba žádné další prostředků vyhledávání nebo zatížení.  Pokud atribut usedList není k dispozici, jsou dostupné všechny Image v pruhu. **Poznámka:** Image může být zadána v jednom z několika formátů, které zahrnují *.bmp*, *.png*, a *.gif*.  Starší verze kompilátoru nepodporuje 32bitové rastrové obrázky, které měly alfa informace pro částečnou průhlednost. Alternativní řešení pro tyto verze se má používat *.png* formátu.|  
|Podmínka|Volitelné. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Podřízené prvky  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Bitmaps – element](../extensibility/bitmaps-element.md)|Seskupí elementy rastrového obrázku.|  
  
## <a name="example"></a>Příklad  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Soubory tabulky (.vsct) příkaz pro Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)