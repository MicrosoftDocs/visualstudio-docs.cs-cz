---
title: Nastavení úložiště Git
description: Použití Gitu a Subversion ve Visual Studiu pro Mac.
author: jmatthiesen
ms.author: jomatthi
ms.date: 02/15/2019
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: 9b21ed322d2b22be619a71e474a3b5078607bbe5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "70107893"
---
# <a name="set-up-a-git-repository"></a>Nastavení úložiště Git

Git je distribuovaný systém správy verzí, který umožňuje týmům pracovat na stejných dokumentech současně. To znamená, že existuje jeden server, který obsahuje všechny soubory, ale vždy, když je úložiště rezervováno z tohoto centrálního zdroje, celé úložiště je klonováno místně do vašeho počítače.

Existuje mnoho vzdálených hostitelů, které vám umožní pracovat s Gitem pro správu verzí, ale nejběžnějším hostitelem je GitHub. Následující příklad používá hostitele GitHubu, ale v Visual Studiu for Mac můžete použít libovolného hostitele Gitu pro správu verzí.

Pokud chcete používat GitHub, ujistěte se, že máte účet vytvořený a nakonfigurovaný před provedením kroků v tomto článku.

## <a name="creating-a-remote-repo-on-github"></a>Vytvoření vzdáleného úložiště na GitHubu

Následující příklad používá hostitele GitHubu, ale v Visual Studiu for Mac můžete použít libovolného hostitele Gitu pro správu verzí.

Chcete-li nastavit úložiště Git, proveďte následující kroky:

1. Vytvořte nové úložiště Git na github.com:

    ![Vytvořit nové úložiště git](media/version-control-git1-sml.png)

2. Nastavte název, popis a ochranu osobních údajů. **Neinicializovat** Repo. Nastavte .gitignore a licenci na žádný:

    ![Nastavení podrobností o úložišti git](media/version-control-git2.png)

3. Na další stránce se zobrazí a zkopíruje adresa HTTPS nebo SSH do vytvořeného repo:

    ![zobrazit a zkopírovat adresu](media/version-control-git3.png)

   Budete potřebovat adresu HTTPS pro převoz Visual Studia pro Mac na toto repo.

## <a name="publishing-an-existing-project"></a>Publikování existujícího projektu

Pokud máte existující projekt, který ještě _není_ ve správě verzí, nastavte ho v Gitu pomocí následujících kroků:

1. Vyberte název řešení z panelu řešení v Sadě Visual Studio pro Mac.

2. Na panelu nabídek vyberte příkaz **Správa verzí > publikování v ovládacím prvku verzí,** aby se zobrazil dialogové okno Vybrat **úložiště:**

    ![Spuštění pokladny ve Visual Studiu pro Mac](media/version-control-git4-sml.png)

    Pokud se tato položka nabídky v nabídce zobrazí šedě, ujistěte se, že jste vybrali název řešení.

3. Zvolte kartu **Registrované úložiště** a stiskněte tlačítko **Přidat:**

    ![](media/version-control-git5.png)

4. Zadejte název úložiště tak, jak chcete, aby se zobrazovalo místně, a vložte adresu URL z kroku #3. Dialogové okno Konfigurace úložiště by mělo vypadat podobně jako následující. Stiskněte tlačítko OK:

    ![Zadejte dialogové okno podrobností gitu](media/version-control-git6.png)

    Je také možné použít SSH pro připojení k Gitu.

5. Chcete-li se pokusit publikovat aplikaci na Git, vyberte úložiště a ujistěte se, že jsou vyplněna textová pole **Název modulu** i **Zpráva:**

    ![Pokus o publikování projektu na git](media/version-control-git7.png)

6. Klikněte na **V pořádku**a potom **na Publish** from the alert dialog .

7. V okně **Přihlašovací údaje Git** zadejte své uživatelské jméno a heslo GitHubu. 

> [!NOTE]
> Pokud je ve vašem účtu povoleno dvoufaktorové ověřování (2FA), budete muset vytvořit přístupový token, který se používá místo hesla. Pokud jste nevytvořili přístupový token, postupujte podle pokynů v dokumentaci [k přístupovému tokenu](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) Git.

8. Zadejte uživatelské jméno a token osobního přístupu a stiskněte **tlačítko Ok**:

    ![Zadejte uživatelské jméno a heslo pro git](media/version-control-git9-sml.png)

9. Po několika sekundách řešení by měla být zveřejněna s jeho počáteční potvrzení. Potvrďte, že byla publikována procházením položky nabídky Správa verzí, která by nyní měla být naplněna mnoha možnostmi:

    ![Nabídka Řízení verzí](media/version-control-git10.png)

10. Jakmile začnete provádět další změny, vyberte **Nabízené změny,** chcete-li změny posunout do **vzdáleného** úložiště. To umožní všem příslušným uživatelům zobrazit na github.com:

    ![Nabízené změny do vzdáleného úložiště](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publikování nového projektu

Dialogové okno nového projektu lze použít k vytvoření nového projektu s místním úložištěm git. Chcete-li ji povolit, zaškrtněte políčko **Použít git pro správu verzí,** jak je znázorněno na následujícím snímku obrazovky. Tím inicializujete úložiště a přidáte volitelný soubor Gitignore:

![Vytvoření nového projektu s podporou git](media/version-control-git-publish-new1.png)

Podle následujících kroků můžete nové místní úložiště převést do nového úložiště GitHubu:

> [!NOTE]
> Pokud jste ještě nevytvořili úložiště GitHub, podívejte se na [vytvoření vzdáleného úložiště na GitHubu](#creating-a-remote-repo-on-github) části.

1. Vytvořte první potvrzení tak, že přejdete na **panel ubírek správy verzí > revizní ho a potvrzeného řešení.**

2. Na kartě Stav zvolte **Potvrdit** v levém horním rohu.

3. Napište zprávu o potvrzení, například "První potvrzení", a klikněte na **Potvrdit**:

    ![Potvrzení počátečních změn v úložišti git](media/version-control-git-publish-new2.png)

4. Dále v panelu nabídek přejděte na **správu verzí > Spravovat větve a dálkové ovladače**.

5. Přejděte na kartu **Vzdálené zdroje** a klikněte na **Přidat**.

6. V okně **Vzdálený zdroj** přidejte podrobnosti o dříve vytvořeném úložišti GitHub a klikněte na **OK**:

    ![Konfigurace vzdálených zdrojů pro úložiště git](media/version-control-git-publish-new3.png)

7. Zavřete okno **Konfigurace úložiště Git** a potom na panelu nabídek přejděte na **položku Správa verzí > Změny push**.

8. V okně **Push to Repository** klikněte na tlačítko **Stisknout změny:**

    ![Posunout změny do vzdáleného úložiště](media/version-control-git-publish-new4.png)

9. Po zobrazení výzvy zadejte uživatelské jméno a heslo GitHubu.

> [!NOTE]
> Pokud je ve vašem účtu povoleno dvoufaktorové ověřování (2FA), budete muset vytvořit přístupový token, který se používá místo hesla. Pokud jste nevytvořili přístupový token, postupujte podle pokynů v dokumentaci [k přístupovému tokenu](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) Git.

Visual Studio pro Mac teď posune změny do vzdáleného úložiště GitHubu:

![Push operace úspěšně dokončena potvrzení](media/version-control-git11.png)

## <a name="check-out-an-existing-repository"></a>Rezervovat existující úložiště

Je pravděpodobné, že budete muset pracovat s úložištěm GitHub, které existuje pouze na dálkovém ovladači, nikoli v místním počítači. Visual Studio pro Mac umožňuje rychle zkontrolovat toto repo. Podle následujících kroků jej naklonujte do počítače:

1. Na panelu nabídek vyberte **položku Správa verzí > pokladna**:

2. Zobrazí se karta **Připojit k úložišti:**

    ![Karta Připojit k úložišti se zadanými podrobnostmi](media/version-control-git13.png)

3. Na stránce GitHub vzdáleného úložiště stiskněte tlačítko **Klonování nebo Stáhnout** a zkopírujte zadaný url:

    ![zobrazí se adresa URL githubu](media/version-control-git14.png)

4. Nahraďte veškerý text v poli položky **adresy URL** na kartě Připojit **k úložišti.** Tím se vyplní většina ostatních polí na této kartě za vás, jak je znázorněno na obrázku v kroku #2.

5. Zadejte adresář, do kterého chcete úložiště naklonovat, a stiskněte **klávesu Pokladna**.

> [!NOTE]
> Pokud je úložiště větší než 4 GB, může dojít k problémům.

## <a name="troubleshooting"></a>Řešení potíží

Pokud máte problémy s inicializací projektu s prázdným vzdáleným úložištěm, můžete zkusit následující kroky:

1. Přejděte do složky řešení.
1. Stiskněte **klávesu Command + Shift + .** zobrazíte skryté soubory a složky.
1. Pokud existuje složka **GIT,** odstraňte ji.
1. Pokud existuje soubor **gitignore,** odstraňte jej.
1. Stiskněte **klávesu Command + Shift + .** skryjete soubory a složky.
1. Otevřete své řešení ve VS for Mac.
1. Na panelu řešení vyberte uzel řešení.
1. Přejděte do nabídky Správa verzí a zvolte **Publikovat v řízení verzí**.
1. Postupujte podle kroků výše uvedeného kurzu od kroku 6.

## <a name="see-also"></a>Viz také

- [Správa verzí v sadě Visual Studio (ve Windows)](/visualstudio/version-control/)
