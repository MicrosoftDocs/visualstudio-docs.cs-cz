---
title: Okna nástrojů v registru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186386"
---
# <a name="tool-windows-in-the-registry"></a>Okna nástrojů v registru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage, které poskytují okna nástrojů, se musí zaregistrovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jako poskytovatelé oken nástrojů. Ve výchozím nastavení se používají okna nástrojů vytvořená pomocí šablony balíčku sady Visual Studio. Poskytovatelé oken nástrojů mají klíče systémového registru, které určují atributy viditelnosti, jako je výchozí velikost a umístění okna nástroje, identifikátor GUID okna, které slouží jako podokno panelu nástrojů, a styl ukotvení.  
  
 Během vývoje jsou poskytovatelé okna spravovaných nástrojů registrovat okna nástrojů přidáním atributů ke zdrojovému kódu a následným spuštěním RegPkg.exeho nástroje ve výsledném sestavení. Další informace najdete v tématu [registrace okna nástroje](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Registrace zprostředkovatelů oken nespravovaných nástrojů  
 Poskytovatelé okna nespravovaného nástroje se musí zaregistrovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] v části ToolWindows systémového registru. Následující fragment souboru REG ukazuje, jak může být zaregistrováno dynamické okno nástroje:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 V prvním klíči v předchozím příkladu je číslo verze verze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , například 7,1 nebo 8,0, podklíč {f0e1e9a1-9860-484d-ad5d-367d79aabf55} je identifikátorem GUID podokna okna nástroje (DynamicWindowPane) a výchozí hodnota {01069cdd-95ce-4620-ac21-ddff6c57f012} je identifikátor GUID VSPackage, který poskytuje okno nástroje. Vysvětlení podklíčů Float a DontForceCreate najdete v tématu [Konfigurace zobrazení okna nástroje](../extensibility/tool-window-display-configuration.md).  
  
 Druhý volitelný klíč, ToolWindows\Visibility, určuje identifikátory GUID příkazů, které vyžadují, aby bylo okno nástroje viditelné. V tomto případě nejsou zadány žádné příkazy. Další informace najdete v tématu [Konfigurace zobrazení v okně nástroje](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Viz také  
 [Základy VSPackage](../misc/vspackage-essentials.md)
