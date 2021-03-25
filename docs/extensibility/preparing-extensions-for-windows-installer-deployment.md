---
title: Příprava rozšíření pro nasazení Instalační služba systému Windows | Microsoft Docs
description: Naučte se, jak připravit projekt, jehož výchozí výstup je balíček VSIX pro zařazení do projektu instalace.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6436d05d3b15be1c1fe8d7c7bb9c8592dee091dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090275"
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
- [Nasazení instalačního programu sady Visual Studio](/previous-versions/2kt85ked(v=vs.120))
- [Návod: Vytvoření vlastní akce](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))