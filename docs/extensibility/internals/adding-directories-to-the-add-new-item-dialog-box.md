---
title: Přidání adresářů do dialogového okna Přidat novou položku | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710256"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Přidání adresářů do dialogového okna Přidat novou položku
Následující příklad kódu ukazuje, jak zaregistrovat novou sadu adresářů pro dialogové okno **Přidat novou položku.** Adresáře pro dialogové okno **Přidat novou položku** se pro každý projekt liší. Adresáře jsou proto registrovány pod podklíčem **Projekty,** který se nachází v **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

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

 Hodnota `%Template_Path%` určuje úplnou cestu k adresáři, který obsahuje šablony projektu. Tyto šablony mohou být buď *.vsz* soubory nebo prototypické soubory šablon, které mají být klonovány.

 Hodnota `SortPriority` určuje prioritu řazení.

## <a name="add-items-to-an-existing-project"></a>Přidání položek do existujícího projektu
 Můžete také přidat položky do existujícího projektu. Pro [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projekt můžete například přidat položky do * \<kořenového>\Soubory programů\Microsoft Visual Studio\VC#\CSharpProjectItems\LocalProjectItems.* V tomto `%GUID_Project%` případě je identifikátor GUID pro projekt Jazyka C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Můžete také rozšířit existující projekt programováním podtypu projektu. Pomocí podtypu projektu můžete rozšířit projekt bez psaní nového typu projektu. Další informace o podtypech projektů naleznete v [tématu Podtypy aplikace Project](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Viz také
- [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)
- [Přidání položek do dialogového okna Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Přidání adresářů do dialogového okna Nový projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
