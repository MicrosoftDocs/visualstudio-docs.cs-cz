---
title: Přidávání adresářů do přidat novou položku – dialogové okno | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ba535908b1c5ccb06f0f29490c0b87c377d6b2be
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498331"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Přidat adresářů do dialogového okna Přidat novou položku
Následující příklad kódu ukazuje, jak registrovat nová sada adresářů pro **přidat novou položku** dialogové okno. Adresáře pro **přidat novou položku** dialogové okno se liší pro každý projekt. Proto zaregistrován v adresářích **projekty** podklíč součástí **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.
  
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
  
 `%Template_Path%` Hodnota určuje úplnou cestu adresáře, který obsahuje šablony projektů. Tyto šablony může být buď *.vsz* soubory nebo soubory šablon typický ke klonování.  
  
 `SortPriority` Hodnota určuje prioritu třídění.  
  
## <a name="add-items-to-an-existing-project"></a>Přidat položky do existujícího projektu  
 Můžete také přidat položky do existujícího projektu. Třeba [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] projektu, můžete přidat položky, které chcete  *\<kořenové > \Program Files\Microsoft \CSharpProjectItems\LocalProjectItems # Visual Studio\VC* složky. V takovém případě `%GUID_Project%` je identifikátor GUID pro projekt C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Můžete také rozšířit existující projekt tím, že podtyp projektu. S podtyp projektu můžete rozšířit projektu, aniž byste museli napsat nový typ projektu. Další informace o podtypů projektů, naleznete v tématu [podtypů projektu](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Viz také:  
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Přidání položek do dialogových oken přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Přidat adresářů do dialogového okna Nový projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)