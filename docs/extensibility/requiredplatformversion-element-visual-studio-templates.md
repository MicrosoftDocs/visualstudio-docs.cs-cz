---
title: Requiredplatformversion – Element (šablony sady Visual Studio) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e040faf4d66d42b107777fd4d57f26c80d040a48
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39635950"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>Requiredplatformversion – element (šablony sady Visual Studio)
Určuje minimální verzi operačního systému, šablonu projektu vyžaduje fungovat správně. Tento element slouží k pro šablony projektů, které vytvářejí [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] aplikace.  
  
 `RequiredPlatformVersion` Se porovnává hodnotu přímo s verzí operačního systému. Pokud `RequiredPlatformVersion` je vyšší než verze operačního systému, šablonu se nezobrazují v **nový projekt** dialogové okno. Chcete-li zadat šablonu pro [!INCLUDE[win8](../debugger/includes/win8_md.md)] nebo vyšší, nastavte `RequiredPlatformVersion` k 6.2.0. Chcete-li zadat šablonu pro [!INCLUDE[win81](../debugger/includes/win81_md.md)] nebo vyšší, nastavte `RequiredPlatformVersion` na 6.3.0.  
  
 Šablony, které určují `RequiredPlatformVersion`= 8 musí být kompatibilní s předchozím zákazníka [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] šablony.  
  
 VSTemplate  
TemplateData  
..... Targetplatformname –  
RequiredPlatformVersion  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Žádné  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené prvky  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené prvky  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Určuje platformu, která šablona cíle projektu.|  
  
## <a name="text-value"></a>Textová hodnota  
 Je vyžadována textová hodnota.  
  
## <a name="remarks"></a>Poznámky  
 Tento text určuje minimální verzi operačního systému vyžadované šablonou.  
  
## <a name="example"></a>Příklad  
 Tento příklad určuje, že projekt cílí šablony [!INCLUDE[win8](../debugger/includes/win8_md.md)] nebo novější.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <TargetPlatformName>Windows</TargetPlatformName>  
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>  
  
    </TemplateData>  
    <TemplateContent>  
  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Targetplatformname – element (šablony sady Visual Studio)](../extensibility/targetplatformname-element-visual-studio-templates.md)   
 [Vytvoření šablon projektů a položek](../ide/creating-project-and-item-templates.md)   
 [Visual Studio odkaz na schéma šablon](../extensibility/visual-studio-template-schema-reference.md)