---
title: Přidání adresářů do dialogového okna Přidat novou položku | Microsoft Docs
description: Naučte se přidávat adresáře do dialogového okna Přidat novou položku v aplikaci Visual Studio pomocí skriptu registru pro registraci adresářů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 68a16d544147ca95512f8b6064d2b9712b26ed64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969019"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Přidání adresářů do dialogového okna Přidat novou položku
Následující příklad kódu ukazuje, jak zaregistrovat novou sadu adresářů pro dialogové okno **Přidat novou položku** . Adresáře pro dialogové okno **Přidat novou položku** se pro každý projekt liší. Proto jsou adresáře registrovány v podklíči **projekty** , které byly nalezeny v **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

## <a name="registry-script"></a>Skript registru

```
NoRemove Projects
{
  NoRemove %GUID_Project%
  {
    NoRemove AddItemTemplates
    {
      NoRemove TemplateDirs
      {
        ForceRemove %CLSID_Package%
        {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
          {
            val TemplatesDir = s '%Template_Path%'
            val SortPriority = d 2000
          }
        }
      }
    }
  }
}
```

 `%Template_Path%`Hodnota určuje úplnou cestu k adresáři, který obsahuje šablony projektu. Tyto šablony můžou být klonovány buď soubory *. vsz* , nebo soubory šablon typický.

 `SortPriority`Hodnota určuje prioritu řazení.

## <a name="add-items-to-an-existing-project"></a>Přidat položky do existujícího projektu
 Můžete také přidat položky do existujícího projektu. Například pro [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projekt můžete přidat položky do složky *\<root> \Program Files\Microsoft Visual Studio\VC # \CSharpProjectItems\LocalProjectItems* . V tomto případě `%GUID_Project%` je identifikátor GUID pro projekt C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Můžete také roztáhnout existující projekt programováním podtypu projektu. S podtypem projektu můžete projekt roztáhnout, aniž byste museli psát nový typ projektu. Další informace o podtypůch projektů naleznete v tématu [podtypy projektu](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Viz také
- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)
- [Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Přidání adresářů do dialogového okna Nový projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
