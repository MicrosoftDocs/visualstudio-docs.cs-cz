---
title: Přidávání adresářů do dialogového okna Přidat novou položku | Microsoft Docs
description: Zjistěte, jak přidat adresáře do dialogového okna Přidat novou položku v Visual Studio pomocí skriptu registru k registraci adresářů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dab135f8e8632755674d7b3ddf5972592f74d315
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904357"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Přidání adresářů do dialogového okna Přidat novou položku
Následující příklad kódu ukazuje, jak zaregistrovat novou sadu adresářů pro dialogové okno **Přidat** novou položku. Adresáře v dialogovém **okně Přidat novou** položku se pro každý projekt liší. Proto jsou adresáře registrovány v podklíči **Projects,** který najdete **vHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

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

 Hodnota `%Template_Path%` určuje úplnou cestu k adresáři, který obsahuje šablony projektů. Tyto šablony mohou být buď *soubory .vsz,* nebo prototypové soubory šablon, které se mají naklonovat.

 Hodnota `SortPriority` určuje prioritu řazení.

## <a name="add-items-to-an-existing-project"></a>Přidání položek do existujícího projektu
 Můžete také přidat položky do existujícího projektu. Například pro projekt můžete přidat položky do složky [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] *\<root> \Program Files\Microsoft Visual Studio\VC#\CSharpProjectItems\LocalProjectItems.* V tomto případě je identifikátor GUID pro projekt `%GUID_Project%` C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Existující projekt můžete také rozšířit programováním podtypu projektu. S podtypem projektu můžete rozšířit projekt bez psaní nového typu projektu. Další informace o podtypech projektů najdete v tématu [Podtypy projektů.](../../extensibility/internals/project-subtypes.md)

## <a name="see-also"></a>Viz také
- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)
- [Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Přidání adresářů do dialogového okna Nový projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
