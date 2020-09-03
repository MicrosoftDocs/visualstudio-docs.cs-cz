---
title: Prvek rastrového obrázku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc1fb57c7ec43421b211b29cfd6ab97b24a1864c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184748"
---
# <a name="bitmap-element"></a>Bitmap – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definuje rastrový obrázek. Rastrový obrázek je načten buď z prostředku, nebo ze souboru.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|guid|Povinná hodnota. Identifikátor GUID identifikátoru příkazu GUID/ID<br /><br /> Atribut GUID rastrového obrázku není přidružen k žádnému VSPackage ani jiné skupině příkazů.  Měl by být jedinečný pro definici rastrového obrázku a neměl by se používat k žádným jiným účelům.|  
|resID|ID identifikátoru příkazu GUID/ID Je požadován buď atribut resID, nebo atribut href.<br /><br /> Atribut resID je ID prostředku typu Integer, které určuje rastrový obrázek, který má být načten během slučování příkazových tabulek.  Při načítání tabulky příkazů se bitmapy zadané ID prostředku načtou z prostředku stejného modulu.|  
|usedList|Vyžaduje se, pokud je přítomen atribut resID. Vybere dostupné obrázky v rastrovém pruhu.|  
|odkaz|Cesta k rastrovému obrázku Je požadován buď atribut resID, nebo atribut href.<br /><br /> Je prohledána cesta include pro zadaný soubor obrázku, který je vložen ve výsledném binárním souboru.  Při sloučení tabulky příkazu se obrázek zkopíruje a nevyžaduje se žádné další vyhledávání nebo načítání prostředků.  Pokud není přítomen atribut usedList, jsou k dispozici všechny obrázky v pruhu. **Poznámka:**  Obrázky mohou být dodávány v jednom z několika formátů, které obsahují soubory. bmp,. png a. gif.  Starší verze kompilátoru nepodporovaly 32 bitové rastrové obrázky, které měly alfa informace pro částečnou průhlednost. Alternativním řešením pro tyto verze je použití formátu. png.|  
|Stav|Nepovinný parametr. Zobrazit [podmíněné atributy](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Bitmaps – element](../extensibility/bitmaps-element.md)|Seskupuje rastrové prvky.|  
  
## <a name="example"></a>Příklad  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Viz také  
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
