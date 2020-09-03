---
title: Přidání adresářů do dialogového okna Přidat novou položku | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f370d208cb8f7aad88f806983983ccee9f584625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203932"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Přidávání adresářů do dialogového okna Přidat novou položku
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následující příklad kódu ukazuje, jak zaregistrovat novou sadu adresářů pro dialogové okno **Přidat novou položku** . Adresáře pro dialogové okno **Přidat novou položku** se pro každý projekt liší. Proto jsou adresáře registrovány v podklíči projekty, nalezeno v \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects> :  
  
## <a name="the-registry-script"></a>Skript registru  
  
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
  
 Hodnota Template_Path Určuje úplnou cestu k adresáři, který obsahuje šablony projektu. Tyto šablony můžou být klonovány buď soubory. vsz, nebo soubory šablon typický.  
  
 Hodnota SortPriority určuje prioritu řazení.  
  
## <a name="adding-items-to-an-existing-project"></a>Přidávání položek do existujícího projektu  
 Můžete také přidat položky do existujícího projektu. Například pro [!INCLUDE[csprcs](../../includes/csprcs-md.md)] projekt můžete přidat položky do \<root> složky \Program Files\Microsoft Visual Studio \VC # \CSharpProjectItems\LocalProjectItems. V tomto případě `%GUID_Project%` je identifikátor GUID pro projekt C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Můžete také roztáhnout existující projekt programováním podtypu projektu. S podtypem projektu můžete projekt roztáhnout, aniž byste museli psát nový typ projektu. Další informace o podtypůch projektů naleznete v tématu [podtypy projektu](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Viz také  
 [Registrace šablon projektů a položek](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Přidávání položek do dialogových oken Přidat novou položku](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Přidávání adresářů do dialogového okna Nový projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
