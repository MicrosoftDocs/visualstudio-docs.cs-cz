---
title: Prostředky v VSPackage | Microsoft Docs
description: Seznamte se s typy lokalizovaných prostředků, které mohou být vloženy do VSPackage. Prostředky můžete také vkládat do nativních knihoven DLL satelitního uživatelského rozhraní nebo spravovaných satelitních knihoven DLL.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 48f88f48f62818882dd15889cdfa1bd2a48d9808
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905822"
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

  Prostředky ve spravovaném balíčku se vyberou podle ID prostředku. Výjimkou je soubor technický ředitel, který musí být pojmenovaný CTMENU. Soubor technický ředitel se musí nacházet v tabulce prostředků jako `byte[]` . Všechny ostatní položky prostředků jsou identifikovány podle typu.

  Můžete použít <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> atribut k označení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spravovaných prostředků, které jsou k dispozici.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Nastavení <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> tímto způsobem označuje, že [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] by měl ignorovat nespravované satelitní knihovny DLL při hledání prostředků, například pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A> . Pokud [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nalezne dva nebo více prostředků, které mají stejné ID prostředku, použije první nalezený prostředek.

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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zpoždění načítání VSPackage, kdykoli je to možné. V důsledku vložení souboru technický ředitel do VSPackage je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nutné načíst všechny takové sady VSPackage v paměti během instalace, což je při sestavení sloučených příkazových tabulek. Prostředky je možné extrahovat ze sady VSPackage tím, že prozkoumáte metadata bez spuštění kódu v VSPackage. Rozhraní VSPackage není v tuto chvíli inicializováno, takže ztráta výkonu je minimální.

 Když aplikace [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] po instalaci vyžádá prostředek ze sady VSPackage, může být tento balíček již načten a inicializován, takže ztráta výkonu je minimální.

## <a name="see-also"></a>Viz také
- [Správa rozšíření VSPackages](../../extensibility/managing-vspackages.md)
- [Lokalizované prostředky v aplikacích MFC: satelitní knihovny DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
