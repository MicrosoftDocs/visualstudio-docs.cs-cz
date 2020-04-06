---
title: Příprava rozšíření pro nasazení Instalační služby systému Windows | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8636dfbbad06192e5edbb61a9a784f64b8f3f14f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702032"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Příprava rozšíření pro nasazení Instalační služby systému Windows
K nasazení balíčku VSIX nelze použít balíček Instalační služby systému Windows (MSI). Můžete však extrahovat obsah balíčku VSIX pro nasazení MSI. Tento dokument ukazuje, jak připravit projekt, jehož výchozí výstup je balíček VSIX pro zahrnutí do projektu instalace.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Příprava projektu rozšíření pro nasazení Instalační služby systému Windows
 Před přidáním do projektu instalace proveďte tyto kroky u nových projektů rozšíření.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Příprava projektu rozšíření pro nasazení Instalační služby systému Windows

1. Vytvořte komponentu VSPackage, MEF, editor adornment nebo jiný typ projektu rozšiřitelnosti, který obsahuje manifest VSIX.

2. Otevřete manifest VSIX v editoru kódu.

3. Nastavte `InstalledByMsi` prvek manifestu VSIX `true`na . Další informace o manifestu VSIX naleznete v [tématu VSIX rozšíření schéma 2.0 odkaz](../extensibility/vsix-extension-schema-2-0-reference.md).

     Tím zabráníte instalačnímu programu VSIX v pokusu o instalaci součásti.

4. Klepněte pravým tlačítkem myši na projekt v **Průzkumníku řešení** a klepněte na příkaz **Vlastnosti**.

5. Vyberte kartu **VSIX.**

6. Zaškrtněte políčko **Kopírovat obsah VSIX do následujícího umístění** a zadejte cestu k místu, kde bude projekt instalace sbírat soubory.

## <a name="extract-files-from-an-existing-vsix-package"></a>Extrahování souborů z existujícího balíčku VSIX
 Provedením těchto kroků přidejte obsah existujícího balíčku VSIX do projektu instalace, pokud nemáte zdrojové soubory.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Extrahování souborů z existujícího balíčku VSIX

1. Přejmenujte *. Soubor VSIX* obsahující příponu z *filename.vsix* na *filename.zip*.

2. Zkopírujte obsah souboru *ZIP* do adresáře.

3. Odstraňte soubor *[Content_types].xml* z adresáře.

4. Upravte manifest VSIX, jak je znázorněno v předchozím postupu.

5. Přidejte zbývající soubory do instalačního projektu.

## <a name="see-also"></a>Viz také
- [Nasazení instalačního programu sady Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Návod: Vytvoření vlastní akce](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
