---
title: Vytvoření balíčku rozšíření
description: Informace o tom, jak vytvořit balíček rozšíření pomocí šablony položky balíčku rozšíření
ms.custom: SEO-VS-2020
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: acangialosi
ms.author: anthc
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: c959660b920abc18be70b228fa6b40de1ab585f8
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037657"
---
# <a name="walkthrough-create-an-extension-pack"></a>Návod: Vytvoření balíčku rozšíření

Balíček rozšíření je sada rozšíření, která se dají nainstalovat dohromady. Balíčky rozšíření umožňují snadno sdílet vaše oblíbená rozšíření s ostatními uživateli nebo seskupit sadu rozšíření dohromady pro konkrétní scénář.

## <a name="prerequisites"></a>Požadavky

Počínaje sadou Visual Studio 2015 je sada Visual Studio SDK zahrnutá jako volitelná funkce v instalačním programu sady Visual Studio. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

Funkce rozšíření Pack je k dispozici počínaje verzí Visual Studio 15,8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Vytvoření rozšíření pomocí šablony položky rozšiřujícího balíčku

Šablona položky balíčku rozšíření vytvoří balíček rozšíření se sadou rozšíření, která lze nainstalovat dohromady.

1. V dialogovém okně **Nový projekt** vyhledejte "VSIX" a vyberte **projekt VSIX**. Jako **název projektu**zadejte "test Extension Pack". Vyberte **Vytvořit**.

2. V **Průzkumník řešení**klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. Přejdete do uzlu **rozšiřitelnost** v jazyce Visual C# a vyberete **rozšíření Pack**. Ponechte výchozí název souboru (ExtensionPack1.cs).

3. Přidal se soubor ExtensionPack1. vsext, který obsahuje následující kód.

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. VsixId rozšíření, které se má zahrnout do balíčku rozšíření, najdete na [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Najděte rozšíření, které chcete zahrnout, a klikněte na **Kopírovat ID**. Existující **vsixId** můžete aktualizovat ve výše uvedeném souboru nebo do seznamu přidat další rozšíření.

    ![Kopírování VsixId z Marketplace](media/vsixid-marketplace.png)

5. Sestavte projekt a nahrajte své rozšíření na Marketplace. Viz [publikování rozšíření aplikace Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Balíček rozšíření může instalovat jenom rozšíření, která jsou k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/) nebo v [soukromé galerii](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Nainstalujte balíček rozšíření z Visual Studio Marketplace

Teď, když je rozšíření publikované, nainstalujte ho v aplikaci Visual Studio a otestujte tam.

::: moniker range="vs-2017"

1. V aplikaci Visual Studio v nabídce **nástroje** klikněte na možnost **rozšíření a aktualizace**.

::: moniker-end

::: moniker range=">=vs-2019"

1. V aplikaci Visual Studio v nabídce **rozšíření** klikněte na **spravovaná rozšíření**.

::: moniker-end

2. Klikněte na **online** a vyhledejte "test Extension Pack".

3. Klikněte na tlačítko **Stáhnout**. Rozšíření a jeho seznam rozšíření, která jsou součástí balíčku rozšíření, se pak naplánují na instalaci.

4. Níže je uveden příklad zobrazení ukázek rozšiřujícího balíčku v dialogovém okně **Spravovat rozšíření** . Pokud dáváte přednost instalaci jenom některých obsažených rozšíření v balíčku rozšíření, můžete upravit seznam rozšíření v části **naplánované pro instalaci**.

    ![Stáhnout rozšiřující balíček z Marketplace](media/vside-extensionpack.png)

5. Chcete-li dokončit instalaci, zavřete všechny instance aplikace Visual Studio.

## <a name="remove-the-extension"></a>Odebrání rozšíření

Odebrání rozšíření z počítače:

::: moniker range="vs-2017"

1. V aplikaci Visual Studio v nabídce **nástroje** klikněte na možnost **rozšíření a aktualizace**.

::: moniker-end

::: moniker range=">=vs-2019"

1. V aplikaci Visual Studio v nabídce **rozšíření** klikněte na **spravovaná rozšíření**.

::: moniker-end

2. Vyberte **Test rozšíření Pack** a pak klikněte na **odinstalovat**. Rozšíření a jeho seznam rozšíření obsažených v balíčku rozšíření se pak naplánují pro odinstalaci.

3. Chcete-li dokončit odinstalaci, zavřete všechny instance aplikace Visual Studio.
