---
title: Templategroupid – Element (šablony sady Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 91631975d48f6e7e13646c428cdd5b5473bbeed2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144434"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID – element (šablony sady Visual Studio)
Určuje, jaký druh projektu šablony položek se zobrazí v. Tento element je důležité, když [ShowByDefault (šablony sady Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) je nastaven na `false`. Když [ShowByDefault (šablony sady Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) je nastaven na `true`, bude k dispozici ve všech typech projektů, šablony položky.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<Templategroupid – >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Rozděluje šablonu a definuje, jak se zobrazuje v buď **nový projekt** nebo **přidat novou položku** dialogové okno.|  
  
## <a name="text-value"></a>Textová hodnota  
 Je vyžadována textová hodnota.  
  
 Text určuje identifikátor pro kategorii šablon položek.  
  
## <a name="remarks"></a>Poznámky  
 `TemplateGroupID` je element.  
  
 Hodnota `TemplateGroupID` element se používá spolu s registrace systému projektu (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<číslo verze >* \Projects\\) Filtr šablon, které se zobrazují v **přidat novou položku** dialogové okno.  
  
|Hodnota Visual C++|Význam|  
|------------------------|-------------|  
|VC Native|Používá pro nativní projekty. Také výchozí Pokud nelze určit typ projektu.|  
|Spravované VC|Použít pro spravované (/ clr) projekty|  
|VC Windows|Použít pro všechny projekty, které cílí na platformu windows (nativní nebo spravovaný/store)|  
|WinRT. nativní UAP|Použít pro Windows 10 úložiště projektů|  
|Nativní CodeSharing|Používá sdílené položky projekty|  
|WinRT. nativní 6.3|Použít pro projekty Windows 8.1 Store|  
|WinRT nativní Phone 6.3|Použít pro projekty Windows Phone 8.1|  
|Nativní WinRT|Použít pro projekty Windows 8.0 Store|  
|VC Android|Používá se systémem Android projekty|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na schéma šablon sady Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)