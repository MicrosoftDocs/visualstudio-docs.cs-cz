---
title: Prostředky v VSPackage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07e1e19f802203b9770764330ea894b7d0eb98b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724159"
---
# <a name="resources-in-vspackages"></a>Prostředky v balíčcích VSPackage
Lokalizované prostředky můžete vkládat do nativních knihoven DLL satelitního uživatelského rozhraní, spravovaných satelitních knihoven DLL nebo ve spravovaném VSPackage.

 Některé prostředky nelze vložit do VSPackage. Je možné vložit následující spravované typy:

- Řetězce

- Klíče načtení balíčku (také řetězce)

- Ikony okna nástrojů

- Soubory výstupu zkompilované tabulky (technický ředitel)

- Rastrové obrázky technický ředitel

- Help příkazového řádku

- O datech dialogových oken

  Prostředky ve spravovaném balíčku se vyberou podle ID prostředku. Výjimkou je soubor technický ředitel, který musí být pojmenovaný CTMENU. Soubor technický ředitel se musí nacházet v tabulce prostředků jako `byte[]`. Všechny ostatní položky prostředků jsou identifikovány podle typu.

  Pomocí atributu <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> můžete určit, že se mají [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tyto spravované prostředky k dispozici.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Nastavení <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> tímto způsobem znamená, že [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] by měl ignorovat nespravované satelitní knihovny DLL při hledání prostředků, například pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Pokud [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zjistí dva nebo více prostředků, které mají stejné ID prostředku, použije první nalezený prostředek.

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
 Pokud je to možné, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prodlevy načítání VSPackage. V důsledku vložení souboru technický ředitel do VSPackage je to, že [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musí načíst všechny takové sady VSPackage v paměti během instalace, což je při sestavení sloučených příkazových tabulek. Prostředky je možné extrahovat ze sady VSPackage tím, že prozkoumáte metadata bez spuštění kódu v VSPackage. Rozhraní VSPackage není v tuto chvíli inicializováno, takže ztráta výkonu je minimální.

 Když [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] požádá o prostředek ze sady VSPackage po instalaci, může být tento balíček již načten a inicializován, takže ztráta výkonu je minimální.

## <a name="see-also"></a>Viz také:
- [Správa rozšíření VSPackages](../../extensibility/managing-vspackages.md)
- [Lokalizované prostředky v aplikacích MFC: Satelitní knihovny DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
