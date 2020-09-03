---
title: Příprava rozšíření pro nasazení Instalační služba systému Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74cfdcaf5b9f9babe9eefed59f1ea62478434e66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85906152"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Příprava rozšíření pro nasazení Instalační služba systému Windows
K nasazení balíčku VSIX nemůžete použít balíček Instalační služba systému Windows (MSI). Můžete však extrahovat obsah balíčku VSIX pro nasazení MSI. Tento dokument ukazuje, jak připravit projekt, jehož výchozí výstup je balíček VSIX pro zařazení do projektu instalace.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Příprava projektu rozšíření pro nasazení Instalační služba systému Windows
 Tyto kroky proveďte v nových projektech rozšíření před přidáním do projektu instalace.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Příprava projektu rozšíření pro nasazení Instalační služba systému Windows

1. Vytvořte VSPackage, komponentu MEF, doplňky editoru nebo jiný typ projektu rozšiřitelnosti, který obsahuje manifest VSIX.

2. Otevřete manifest VSIX v editoru kódu.

3. Nastavte `InstalledByMsi` prvek MANIFESTU VSIX na `true` . Další informace o manifestu VSIX najdete v referenčních informacích k [schématu rozšíření vsix 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).

     To brání instalačnímu programu VSIX v pokusu o instalaci součásti.

4. Klikněte pravým tlačítkem na projekt v **Průzkumník řešení** a klikněte na **vlastnosti**.

5. Vyberte kartu **VSIX** .

6. Zaškrtněte políčko **Kopírovat obsah VSIX do následujícího umístění** a zadejte cestu k umístění, kam projekt instalace zachová soubory.

## <a name="extract-files-from-an-existing-vsix-package"></a>Extrakce souborů z existujícího balíčku VSIX
 Provedením těchto kroků přidáte obsah existujícího balíčku VSIX do projektu instalace, pokud nemáte zdrojové soubory.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Extrakce souborů z existujícího balíčku VSIX

1. Přejmenujte *. Soubor VSIX* obsahující rozšíření z *souboru filename. vsix* pro *filename.zip*.

2. Zkopírujte obsah souboru *. zip* do adresáře.

3. Odstraňte soubor *[Content_Types]. XML* z adresáře.

4. Upravte manifest VSIX, jak je znázorněno v předchozím postupu.

5. Přidejte zbývající soubory do projektu instalace.

## <a name="see-also"></a>Viz také
- [Nasazení instalačního programu sady Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Návod: Vytvoření vlastní akce](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
