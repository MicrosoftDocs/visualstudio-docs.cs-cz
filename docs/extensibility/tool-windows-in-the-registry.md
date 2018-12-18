---
title: Nástroje systému Windows v registru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 234a3f50865e77f2c6b5a4057e6766b26d7ff521
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138444"
---
# <a name="tool-windows-in-the-registry"></a>Nástroje systému Windows v registru
VSPackages, které poskytují nástroje systému windows musíte zaregistrovat u [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jako nástroj okno zprostředkovatele. Nástroje systému windows vytvořených pomocí šablony balíček Visual Studio k tomu ve výchozím nastavení. Okno poskytovatelů nástrojů mít klíče registru systému, které určit viditelnost atributy, jako je například výchozí velikost okna nástroje a umístění, identifikátor GUID okně, které slouží jako nástroj podokna a styl ukotvení.  
  
 Během vývoje zaregistrovat poskytovatelů okno spravované nástrojů okna nástrojů přidáním atributy ke zdrojovému kódu a potom spustí nástroj RegPkg.exe ve výsledné sestavení. Další informace najdete v tématu [registrace okno nástroje](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrace zprostředkovatele okno nespravované nástroj  
 Zprostředkovatelé okno nespravované nástroj musíte zaregistrovat u [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] v části ToolWindows systémový registr. Následující fragment souboru .reg ukazuje, jak může zaregistrovat okno dynamické nástroje:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 V první klíč v příkladu nahoře, číslo verze je verze [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], například 7.1 nebo 8.0, podklíč {f0e1e9a1-9860-484d-ad5d-367d79aabf55} je identifikátor GUID podokně okna nástroj (DynamicWindowPane) a {hodnotu výchozí 01069cdd-95ce-4620-ac21-ddff6c57f012} je identifikátor GUID VSPackage poskytování okno nástroje. Vysvětlení podklíče Float a DontForceCreate naleznete v tématu [konfigurace zobrazení okna nástroj](../extensibility/tool-window-display-configuration.md).  
  
 Druhý volitelné klíč ToolWindows\Visibility, určuje identifikátory GUID příkazy, které vyžadují panel nástrojů, který má být viditelné. V tomto případě nejsou žádné příkazy zadané. Další informace najdete v tématu [konfigurace zobrazení okna nástroj](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Viz také  
 [Balíčky VSPackage](../extensibility/internals/vspackages.md)