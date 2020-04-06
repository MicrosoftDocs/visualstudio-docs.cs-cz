---
title: Přidání adresářů do dialogového okna Nový projekt | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 827e383bba13c9742deb654bf3d680adeb3c109b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710236"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Přidání adresářů do dialogového okna Nový projekt
Při vytváření nových typů projektů můžete také zaregistrovat nový adresář v dialogovém okně **Nový projekt** a zobrazit je pro použití jako šablony. Následující příklad kódu vysvětluje, jak zaregistrovat nový adresář, označovaný také jako uzel. V příkladu jsou registrovány šablony vystavené VSPackage, *CLSID_Package*. V důsledku toho nabízí levá strana dialogového okna **Nový projekt** přidaný uzel s názvem určeným *Folder_Label_ResID* zdrojem. Tento prostředek je načten ze satelitní dll satelitní ho balíčku VSPackage.

 Hodnota **Folder** představuje identifikátor GUID složky, pod kterou je zobrazen *uzel Folder_Label_ResID.* V příkladu představuje identifikátor GUID složku **Ostatní projekty** v podokně **Typy projektů** dialogového okna **Nový projekt.** Pokud chybí hodnota **Jiné projekty,** popisek je umístěn na nejvyšší úrovni.

 Hodnota `TemplatesDir` určuje úplnou cestu k adresáři, který obsahuje šablony projektu. Tyto soubory mohou být buď *.vsz* soubory nebo typické soubory šablony, které mají být klonovány.

 Pokud zadáte `TemplatesLocalizedSubDir`, musí to být ID prostředku řetězce, `TemplatesDir` který pojmenovává podadresář, který obsahuje lokalizované šablony. Vzhledem k tomu, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] že načte řetězec prostředek ze satelitní dll, pokud máte jeden, každý satelitní DLL může obsahovat jiný název podadresáře. Hodnota `SortPriority` určuje prioritu řazení.

```
NoRemove NewProjectTemplates
{
    NoRemove TemplateDirs
  {
    ForceRemove %CLSID_Package%
    {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
      {
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'
        val TemplatesDir = s '%Template_Path%'
        val TemplatesLocalizedSubDir = s '#100'
        val SortPriority = d 1000
      }
    }
  }
}
```

## <a name="see-also"></a>Viz také
- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)
- [Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Přidání adresářů do dialogového okna Přidat novou položku](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
