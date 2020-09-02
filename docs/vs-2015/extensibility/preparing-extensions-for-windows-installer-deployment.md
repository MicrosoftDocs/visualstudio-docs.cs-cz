---
title: Příprava rozšíření pro nasazení Instalační služba systému Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 76d7f879fade99914bf3f56ade0ec1270e14f4c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694594"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Příprava rozšíření pro nasazení Instalační služby systému Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

K nasazení balíčku VSIX nemůžete použít balíček Instalační služba systému Windows (MSI). Můžete však extrahovat obsah balíčku VSIX pro nasazení MSI. Tento dokument ukazuje, jak připravit projekt, jehož výchozí výstup je balíček VSIX pro zařazení do projektu instalace.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Příprava projektu rozšíření pro nasazení Instalační služba systému Windows  
 Tyto kroky proveďte v nových projektech rozšíření před přidáním do projektu instalace.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Příprava projektu rozšíření pro nasazení Instalační služba systému Windows  
  
1. Vytvořte VSPackage, komponentu MEF, doplňky editoru nebo jiný typ projektu rozšiřitelnosti, který obsahuje manifest VSIX.  
  
2. Otevřete manifest VSIX v editoru kódu.  
  
3. Nastavte element InstalledByMsi manifestu VSIX na `true` . Další informace o manifestu VSIX najdete v referenčních informacích k [schématu rozšíření vsix 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     To brání instalačnímu programu VSIX v pokusu o instalaci součásti.  
  
4. Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a klikněte na **vlastnosti**.  
  
5. Vyberte kartu **VSIX** .  
  
6. Zaškrtněte políčko **Kopírovat obsah VSIX do následujícího umístění** a zadejte cestu k umístění, kam projekt instalace zachová soubory.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Extrakce souborů z existujícího balíčku VSIX  
 Provedením těchto kroků přidáte obsah existujícího balíčku VSIX do projektu instalace, pokud nemáte zdrojové soubory.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Extrakce souborů z existujícího balíčku VSIX  
  
1. Přejmenujte. Soubor VSIX obsahující rozšíření z *souboru filename*. vsix do *souboru filename*. zip  
  
2. Zkopírujte obsah souboru. zip do adresáře.  
  
3. Odstraňte soubor [Content_types]. XML z adresáře.  
  
4. Upravte manifest VSIX, jak je znázorněno v předchozím postupu.  
  
5. Přidejte zbývající soubory do projektu instalace.  
  
## <a name="see-also"></a>Viz také  
 [Nasazení Instalační program pro Visual Studio](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Návod: Vytvoření vlastní akce](https://msdn.microsoft.com/4bd4b63a-2b91-431e-839c-5752443f0eaf)
