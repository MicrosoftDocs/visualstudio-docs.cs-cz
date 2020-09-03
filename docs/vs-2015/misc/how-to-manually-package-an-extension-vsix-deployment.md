---
title: 'Postupy: ruční zabalení rozšíření (nasazení VSIX) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: d25990e0-e782-4a79-9d9a-1caf3c56c6a2
caps.latest.revision: 10
manager: jillfra
ms.openlocfilehash: a615aea75ec00e49ee4d2837b8b4e2b1d20d3306
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74293619"
---
# <a name="how-to-manually-package-an-extension-vsix-deployment"></a>Postupy: ruční zabalení rozšíření (nasazení VSIX)
Můžete vytvořit balíček VSIX, který zabalí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozšíření pro nasazení. Existují tři způsoby, jak vytvořit balíček:  
  
- Vytvořte projekt VSIX Package pomocí jedné ze šablon rozšiřitelnosti, které jsou součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sady SDK. Toto je nejjednodušší způsob pro většinu scénářů.  
  
- Zabalte výstup projektu rozšíření do prázdného [projektu VSIX](../extensibility/vsix-project-template.md). Tuto možnost doporučujeme pro šablony, nepodporovaná sestavení a vlastní typy.  
  
- Ruční vytvoření balíčku VSIX Tuto možnost doporučujeme jenom v případě, že nejsou k dispozici jiné dvě možnosti.  
  
  Tento dokument popisuje třetí možnost.  
  
## <a name="creating-a-vsix-package"></a>Vytvoření balíčku VSIX  
 Chcete-li ručně zabalit rozšíření, přidejte soubor s příponou. manifest a soubor [Content_Types]. XML do projektu rozšíření, umístěte je do komprimovaného souboru společně s výstupem sestavení a přejmenujte komprimovaný soubor tak, aby měl příponu názvu souboru. VSIX. Rozšíření, které má být zabaleno, musí být typu, který je podporován [schématem VSIX](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b).  
  
> [!NOTE]
> Názvy souborů v balíčcích VSIX nesmí obsahovat mezery, ani znaky, které jsou vyhrazené v identifikátorech URI (Uniform Resource Identifier), jak je definováno v [ \[ RFC2396 \] ](https://go.microsoft.com/fwlink/?LinkId=90339).  
  
#### <a name="to-manually-create-a-vsix-package"></a>Ruční vytvoření balíčku VSIX  
  
1. Vytvořte rozšíření sady Visual Studio typu, který je podporován schématem VSIX.  
  
2. Vytvořte soubor XML a pojmenujte ho `extension.vsixmanifest` .  
  
3. Do souboru extension. vsixmanifest zadejte v závislosti na schématu VSIX. Příklad manifestu naleznete v tématu [PackageManifest element (root element, VSX Schema)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187).  
  
4. Vytvořte druhý soubor XML a pojmenujte ho `[Content_Types].xml` .  
  
5. Do souboru [Content_Types]. XML zadejte, jak je uvedeno ve [struktuře \] souboru Content_Types. XML](../extensibility/the-structure-of-the-content-types-dot-xml-file.md).  
  
6. Soubory XML umístěte do adresáře společně s příponou, která se má nasadit.  
  
     V případě šablony projektu nebo šablony položky vložte soubor. zip, který obsahuje šablonu, do stejné složky jako soubory XML. Neumísťujte soubory XML do souboru. zip.  
  
     Ve všech ostatních případech Vložte soubory XML do stejného adresáře jako výstup sestavení.  
  
7. V Průzkumníku Windows klikněte pravým tlačítkem na složku, která obsahuje obsah rozšíření a dva soubory XML, klikněte na **Odeslat do**a pak klikněte na **Komprimovaná složka (ZIP)**.  
  
8. Přejmenujte výsledný soubor. zip na *filename*. vsix, kde *filename* je název redistribuovatelného souboru, který nainstaluje balíček.  
  
## <a name="see-also"></a>Viz také  
 [Expedice rozšíření sady Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [PackageManifest – element (kořenový element, schéma VSX)](https://msdn.microsoft.com/f8ae42ba-775a-4d2b-976a-f556e147f187)