---
title: 'Postupy: ruční balíček rozšíření (nasazení VSIX) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: douge
ms.openlocfilehash: 0d10d0e49389b43a288826adf2043c603aeff36a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925835"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>Postupy: ruční balíček rozšíření (VSIX nasazení)
Můžete vytvořit balíček VSIX zabalit [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření pro nasazení. Existují tři způsoby, jak vytvořit balíček:  
  
- Vytvořte projekt VSIX balíček pomocí jedné z, které jsou součástí šablony pro rozšiřující [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK. Toto je nejjednodušší způsob pro většinu scénářů.  
  
- Zabalení výstup projektu rozšíření v prázdné [projekt VSIX](../extensibility/vsix-project-template.md). Doporučujeme tuto možnost pro šablony, nepodporované sestavení a vlastních typů.  
  
- Ruční vytvoření balíčku VSIX. Tuto možnost doporučujeme pouze v případě, že nejsou k dispozici dvě možnosti.  
  
  Tento dokument popisuje třetí možnost.  
  
## <a name="creating-a-vsix-package"></a>Vytvoření balíčku VSIX  
 Chcete-li ručně balíček rozšíření, přidat soubor s příponou extension.manifest a souboru [Content_Types] .xml do projektu rozšíření, vytvořte z nich v komprimovaném souboru spolu s výstupu sestavení a přejmenujte komprimovaný soubor tak, aby měl příponu názvu souboru .vsix. Rozšíření zabalit, musí být typu, který je podporován [VSIX schématu](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
> [!NOTE]
>  Názvy souborů v balíčků VSIX nesmí obsahovat mezery ani znaky, které jsou vyhrazené v identifikátory URI (Uniform Resource), jako jsou definované v části [ \[RFC2396\]](http://go.microsoft.com/fwlink/?LinkId=90339).  
  
#### <a name="to-manually-create-a-vsix-package"></a>Ruční vytvoření balíčku VSIX  
  
1.  Vytvoření rozšíření sady Visual Studio typu, který je podporován schématu VSIX.  
  
2.  Vytvořte soubor XML s názvem `extension.vsixmanifest`.  
  
3.  Zadejte soubor extension.vsixmanifest podle schématu VSIX. Manifest příklad naleznete v tématu [PackageManifest – Element (kořenový Element, schéma VSX)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4.  Vytvořte druhý soubor XML s názvem `[Content_Types].xml`.  
  
5.  Vyplňte souboru [Content_Types] .xml uvedená v [struktura Content_types\]XML soubor](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
6.  Vložte oba soubory XML adresáře spolu s příponou k nasazení.  
  
     V případě šablona projektu nebo šablony položky umístěte soubor .zip, který obsahuje šablonu ve stejné složce jako soubor XML. Neumisťujte soubory XML v souboru ZIP.  
  
     Soubory XML ve všech ostatních případech lze umístěte do stejného adresáře jako výstup sestavení.  
  
7.  V Průzkumníku Windows, klikněte pravým tlačítkem na složku, která obsahuje rozšíření obsahu a dva soubory XML, klikněte na tlačítko **odeslat**a potom klikněte na tlačítko **komprimovaná složka (metoda ZIP)**.  
  
8.  Přejmenovat výsledný soubor ZIP do *Filename*VSIX, kde *Filename* je název redistribuovatelného souboru, který nainstaluje balíček.  
  
## <a name="see-also"></a>Viz také  
 [Přesouvání rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Element PackageManifest (kořenový Element, schéma VSX)](http://msdn.microsoft.com/en-us/f8ae42ba-775a-4d2b-976a-f556e147f187)