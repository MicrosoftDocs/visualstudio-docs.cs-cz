---
title: Prostředky v VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90674d17cdc3fb8956fd6eedeb3acb27226620cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696089"
---
# <a name="resources-in-vspackages"></a>Prostředky v balíčcích VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lokalizované prostředky můžete vkládat do nativních knihoven DLL satelitního uživatelského rozhraní, spravovaných satelitních knihoven DLL nebo ve spravovaném VSPackage.  
  
 Některé prostředky nelze vložit do VSPackage. Je možné vložit následující spravované typy:  
  
- Řetězce  
  
- Klíče načtení balíčku (také řetězce)  
  
- Ikony okna nástrojů  
  
- Soubory výstupu zkompilované tabulky (technický ředitel)  
  
- Rastrové obrázky technický ředitel  
  
- Help příkazového řádku  
  
- O datech dialogových oken  
  
  Prostředky ve spravovaném balíčku se vyberou podle ID prostředku. Výjimkou je soubor technický ředitel, který musí být pojmenovaný CTMENU. Soubor technický ředitel se musí nacházet v tabulce prostředků jako `byte[]` . Všechny ostatní položky prostředků jsou identifikovány podle typu.  
  
  Můžete použít <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> atribut k označení [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spravovaných prostředků, které jsou k dispozici.  
  
  [!code-csharp[VSSDKResources#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkresources/cs/vssdkresourcespackage.cs#1)]
  [!code-vb[VSSDKResources#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkresources/vb/vssdkresourcespackage.vb#1)]  
  
  Nastavení <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> tímto způsobem označuje, že [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] by měl ignorovat nespravované satelitní knihovny DLL při hledání prostředků, například pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . Pokud [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nalezne dva nebo více prostředků, které mají stejné ID prostředku, použije první nalezený prostředek.  
  
## <a name="example"></a>Příklad  
 Následující příklad je spravovaná reprezentace ikony okna nástroje.  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 Následující příklad ukazuje, jak vložit pole technický ředitel Byte, které musí mít název CTMENU.  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>Poznámky k implementaci  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zpoždění načítání VSPackage, kdykoli je to možné. V důsledku vložení souboru technický ředitel do VSPackage je [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nutné načíst všechny takové sady VSPackage v paměti během instalace, což je při sestavení sloučených příkazových tabulek. Prostředky je možné extrahovat ze sady VSPackage tím, že prozkoumáte metadata bez spuštění kódu v VSPackage. Rozhraní VSPackage není v tuto chvíli inicializováno, takže ztráta výkonu je minimální.  
  
 Když aplikace [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] po instalaci vyžádá prostředek ze sady VSPackage, může být tento balíček již načten a inicializován, takže ztráta výkonu je minimální.  
  
## <a name="see-also"></a>Viz také  
 [Spravované VSPackage](../../misc/managed-vspackages.md)   
 [Správa VSPackage](../../extensibility/managing-vspackages.md)   
 [Lokalizované prostředky v aplikacích MFC: satelitní knihovny DLL](https://msdn.microsoft.com/library/3a1100ae-a9c8-47b5-adbd-cbedef5992ef)   
 [Spravované VSPackage](../../misc/managed-vspackages.md)
