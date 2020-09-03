---
title: Přidání adresářů do dialogového okna Přidat novou položku | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d4af79f95c87271e9a10eece6c728daa9a81305
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710256"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Přidání adresářů do dialogového okna Přidat novou položku
Následující příklad kódu ukazuje, jak zaregistrovat novou sadu adresářů pro dialogové okno **Přidat novou položku** . Adresáře pro dialogové okno **Přidat novou položku** se pro každý projekt liší. Proto jsou adresáře registrovány v podklíči **projekty** , které byly nalezeny v **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0Exp\Projects**.

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
 Můžete také přidat položky do existujícího projektu. Například pro [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projekt můžete přidat položky do složky * \<root> \Program Files\Microsoft Visual Studio\VC # \CSharpProjectItems\LocalProjectItems* . V tomto případě `%GUID_Project%` je identifikátor GUID pro projekt C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Můžete také roztáhnout existující projekt programováním podtypu projektu. S podtypem projektu můžete projekt roztáhnout, aniž byste museli psát nový typ projektu. Další informace o podtypůch projektů naleznete v tématu [podtypy projektu](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Viz také
- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)
- [Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Přidání adresářů do dialogového okna Nový projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
