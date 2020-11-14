---
title: Práce s účty GitHub v aplikaci Visual Studio
ms.date: 11/13/2020
ms.custom: ''
ms.topic: conceptual
description: Naučte se používat Visual Studio s účty GitHubu.
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: d0575abb528810e714dbe747b46db986dc3ce6e1
ms.sourcegitcommit: c1cc3d8e1673c52fbfddc86b089b4a3d46bb3e59
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2020
ms.locfileid: "94631610"
---
# <a name="work-with-github-accounts-in-visual-studio"></a>Práce s účty GitHub v aplikaci Visual Studio

Pokud máte veřejný účet GitHubu nebo GitHub Enterprise, můžete ho přidat do řetězce klíčů sady Visual Studio. Po přidání účtu budete moct využít výhod integrace platformy tím, že budete mít přístup k úložištím GitHubu přímo ze sady Visual Studio a vytváříte je.  

## <a name="adding-public-github-accounts"></a>Přidávání veřejných účtů GitHubu

Svůj veřejný účet GitHub můžete přidat, pokud jste už přihlášení k aplikaci Visual Studio pomocí účet Microsoft nebo pracovního nebo školního účtu.

1. Vyberte ikonu s vašimi iniciálami v pravém horním rohu prostředí sady Visual Studio. Pak vyberte **Nastavení účtu...** pro správu účtů. Můžete také otevřít dialogové okno nastavení účtu, a to tak **File** , že kliknete na  >  **Nastavení účtu** souboru.

    :::image type="content" source="../ide/media/account-picker.png" alt-text="Nastavení účtu":::

2. V podnabídce **všechny účty** vyberte znaménko plus a přidejte účet a vyberte **GitHub**.

    :::image type="content" source="../ide/media/sign-in-add-github.png" alt-text="Vyberte Přidat účet GitHub.":::

3. Budete přesměrováni do prohlížeče, kde se můžete přihlásit pomocí přihlašovacích údajů GitHubu. Po přihlášení se zobrazí okno úspěch v prohlížeči a můžete se vrátit do sady Visual Studio.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="Okno úspěch v prohlížeči":::

4. V podnabídce **všechny účty** budou k dispozici oba účty.

    :::image type="content" source="../ide/media/show-both-accounts.png" alt-text="Oba účty ukazují":::

Pokud ještě nejste přihlášení k aplikaci Visual Studio s jiným účtem, vyberte odkaz **Přihlásit** se v pravém horním rohu prostředí sady Visual Studio. Můžete také otevřít dialogové okno nastavení účtu, a to tak **File** , že kliknete na  >  **Nastavení účtu** souboru. Pak podle výše uvedených pokynů přidejte svůj účet GitHub.

![Přihlášený uživatel](../ide/media/vs2019_usernotsignedin.png)

## <a name="adding-github-enterprise-accounts"></a>Přidávání účtů GitHub Enterprise

Ve výchozím nastavení má Visual Studio povolené jenom veřejné účty GitHubu.

1. Pokud chcete povolit účty na webu GitHub Enterprise **Tools** , klikněte na  >  **Možnosti** nástroje a vyhledejte možnosti **účtů** .

    :::image type="content" source="../ide/media/accounts-options.png" alt-text="Nabídka možnosti účtů":::

2. Potom zaškrtněte políčko, aby **zahrnovalo účty GitHub Enterprise serveru**. Až příště přejdete do **Nastavení účtu** a zkusíte přidat účet GitHubu, uvidíte možnosti pro GitHub i GitHub Enterprise.

    :::image type="content" source="../ide/media/github-enterprise-endpoint-signin.png" alt-text="Přihlaste se pomocí GitHubu Enterprise":::

3. Po zadání adresy serveru GitHub Enterprise vyberte možnost **Přihlásit se pomocí prohlížeče**. V takovém případě se můžete přihlásit pomocí svých přihlašovacích údajů pro GitHub Enterprise.

## <a name="see-also"></a>Viz také

- [Práce s několika uživatelskými účty](work-with-multiple-user-accounts.md)
- [Přihlášení k sadě Visual Studio](signing-in-to-visual-studio.md)
