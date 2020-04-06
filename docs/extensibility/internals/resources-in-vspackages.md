---
title: Zdroje v balíčcích VSPackages | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 493e9834e3d7cf6d82cebb8dd93d5369678c7be0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705604"
---
# <a name="resources-in-vspackages"></a>Prostředky v balíčcích VSPackage
Lokalizované prostředky můžete vložit do nativních satelitních knihoven DLL, spravovaných satelitních knihoven DLL nebo do spravovaného balíčku VSPackage.

 Některé prostředky nelze vložit do VSPackages. Lze vložit následující spravované typy:

- Řetězce

- Klíče pro načítání balíčků (které jsou také řetězce)

- Ikony oken nástrojů

- Soubory zkompilované hospodařilocí tabulky příkazů (CTO)

- Bitmapy KTo

- Nápověda k příkazovému řádku

- Data dialogového okna O

  Prostředky ve spravovaném balíčku jsou vybrány podle ID prostředku. Výjimkou je soubor CTO, který musí být pojmenován CTMENU. Soubor CTO se musí zobrazit v `byte[]`tabulce zdrojů jako . Všechny ostatní položky zdroje jsou identifikovány podle typu.

  <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> Atribut můžete použít k [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] označení, že spravované prostředky jsou k dispozici.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Nastavení <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> tímto způsobem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] znamená, že by měl ignorovat nespravované satelitní knihovny <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>DLL při hledání prostředků, například pomocí . Pokud [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dojde ke dvěma nebo více prostředků, které mají stejné ID prostředku, použije první prostředek, který najde.

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

 Následující příklad ukazuje, jak vložit pole bajtu Čtv, které musí být pojmenováno CTMENU.

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

## <a name="implementation-notes"></a>Poznámky k provádění
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zpoždění načítání VSPackages, kdykoli je to možné. Důsledkem vložení souboru CTO do balíčku VSPackage je, že [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musí načíst všechny tyto VSPackages v paměti během instalace, což je při sestavení sloučené příkazové tabulky. Prostředky lze extrahovat z VSPackage kontrolou metadat bez spuštění kódu v Balíčku VSPackage. VSPackage není inicializována v tomto okamžiku, takže ztráta výkonu je minimální.

 Při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] požadavku na prostředek z VSPackage po instalaci, tento balíček je pravděpodobné, že již načtena a inicializována, takže ztráta výkonu je minimální.

## <a name="see-also"></a>Viz také
- [Správa rozšíření VSPackages](../../extensibility/managing-vspackages.md)
- [Lokalizované prostředky v aplikacích MFC: Satelitní knihovny DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
