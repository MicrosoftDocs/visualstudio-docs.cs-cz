---
title: Příprava rozšíření pro nasazení Instalační služby systému Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cc742fecbbe03ff3d3aa0fb3f8d61a9c5f09254b
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495268"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Příprava rozšíření pro nasazení Instalační služby systému Windows
Balíček Instalační služby systému Windows (MSI) nelze použít k nasazení balíčku VSIX. Můžete však extrahovat obsah balíčku VSIX pro nasazení MSI. Tento dokument ukazuje, jak připravit projektu, jehož výchozí výstup je balíčku VSIX pro zahrnutí do projektu instalace.  
  
## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Příprava rozšíření projektu pro nasazení Instalační služby systému Windows  
 Tyto kroky provádíte u nových projektů rozšíření před přidáním do projektu instalace.  
  
### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Příprava rozšíření projektu nasazení Instalační služby systému Windows  
  
1.  Vytvoření VSPackage, součást MEF, dalších úprav editoru nebo jiný typ projektu rozšiřitelnosti, který obsahuje VSIX manifest.  
  
2.  VSIX manifest se otevře v editoru kódu.  
  
3.  Nastavte `InstalledByMsi` elementu v manifestu VSIX do `true`. Další informace o manifestu VSIX, který najdete v tématu [VSIX extension schema 2.0 – referenční informace](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     To zabrání instalátor VSIX pokusu o instalaci komponenty.  
  
4.  Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a klikněte na tlačítko **vlastnosti**.  
  
5.  Vyberte **VSIX** kartu.  
  
6.  Zaškrtněte políčko **VSIX kopírování obsahu do následujícího umístění** a zadejte cestu, kde bude projekt instalace přinutili soubory.  
  
## <a name="extract-files-from-an-existing-vsix-package"></a>Extrahujte soubory z existujícího balíčku VSIX  
 Proveďte tyto kroky, které chcete přidat obsah existujícího balíčku VSIX k projektu instalace, když nemáte zdrojové soubory.  
  
### <a name="to-extract-files-from-an-existing-vsix-package"></a>Extrahujte soubory z existujícího balíčku VSIX  
  
1.  Přejmenovat *. VSIX* soubor, který obsahuje rozšíření z *filename.vsix* k *filename.zip*.  
  
2.  Zkopírujte obsah *ZIP* soubor do adresáře.  
  
3.  Odstranit *[Content_types] .xml* soubor z adresáře.  
  
4.  Upravte VSIX manifest, jak je znázorněno v předchozím postupu.  
  
5.  Přidejte do projektu instalace zbývající soubory.  
  
## <a name="see-also"></a>Viz také:  
 [Nasazení instalačního programu sady Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Návod: Vytvoření vlastní akce](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))