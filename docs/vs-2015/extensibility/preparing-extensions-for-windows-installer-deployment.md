---
title: Příprava rozšíření pro nasazení Instalační služby systému Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 90dc7fb0ca361e6c1994cfd7108b171cda2ad1f9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755107"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Příprava rozšíření pro nasazení Instalační služby systému Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Balíček Instalační služby systému Windows (MSI) nelze použít k nasazení balíčku VSIX. Můžete však extrahovat obsah balíčku VSIX pro nasazení MSI. Tento dokument ukazuje, jak připravit projektu, jehož výchozí výstup je balíčku VSIX pro zahrnutí do projektu instalace.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Příprava rozšíření projektu pro nasazení Instalační služby systému Windows  
 Tyto kroky provádíte u nových projektů rozšíření před přidáním do projektu instalace.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Příprava rozšíření projektu nasazení Instalační služby systému Windows  
  
1.  Vytvoření VSPackage, součást MEF, dalších úprav editoru nebo jiný typ projektu rozšiřitelnosti, který obsahuje VSIX manifest.  
  
2.  VSIX manifest se otevře v editoru kódu.  
  
3.  Nastavte element InstalledByMsi v manifestu VSIX do `true`. Další informace o manifestu VSIX, který najdete v tématu [VSIX Extension Schema 2.0 referenční informace](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     To zabrání instalátor VSIX pokusu o instalaci komponenty.  
  
4.  Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a klikněte na tlačítko **vlastnosti**.  
  
5.  Vyberte **VSIX** kartu.  
  
6.  Zaškrtněte políčko **VSIX kopírování obsahu do následujícího umístění** a zadejte cestu, kde bude projekt instalace přinutili soubory.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Extrahování souborů z existujícího balíčku VSIX  
 Proveďte tyto kroky, které chcete přidat obsah existujícího balíčku VSIX k projektu instalace, když nemáte zdrojové soubory.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Extrahujte soubory z existujícího balíčku VSIX  
  
1.  Přejmenovat. Soubor VSIX, který obsahuje rozšíření z *filename*VSIX do *filename*.zip.  
  
2.  Zkopírujte obsah souboru ZIP do adresáře.  
  
3.  Odstranění souboru [Content_types] .xml z adresáře.  
  
4.  Upravte VSIX manifest, jak je znázorněno v předchozím postupu.  
  
5.  Přidejte do projektu instalace zbývající soubory.  
  
## <a name="see-also"></a>Viz také  
 [Nasazení instalačního programu sady Visual Studio](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Návod: Vytvoření vlastní akce](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)

