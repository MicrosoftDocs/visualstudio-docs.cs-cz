---
title: Nastavení úložiště Git
description: Použití Gitu a podverze v Visual Studio pro Mac.
author: therealjohn
ms.author: johmil
ms.date: 05/13/2020
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.topic: how-to
ms.openlocfilehash: bc981530f5493ce1899de1c888e20129c7ae0f8c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88214697"
---
# <a name="set-up-a-git-repository"></a>Nastavení úložiště Git

Git je distribuovaný systém správy verzí, který umožňuje týmům současně pracovat na stejných dokumentech. To znamená, že existuje jeden server, který obsahuje všechny soubory, ale kdykoli je úložiště rezervované z tohoto centrálního zdroje, celé úložiště se naklonuje místně do vašeho počítače.

Existuje mnoho vzdálených hostitelů, které vám umožňují pracovat s Git pro správu verzí, ale nejběžnější hostitel je GitHub. Následující příklad používá hostitele GitHub, ale můžete použít libovolného hostitele Git pro správu verzí v Visual Studio pro Mac.

Pokud chcete použít GitHub, ujistěte se, že máte vytvořený a nakonfigurovaný účet před provedením kroků v tomto článku.

## <a name="creating-a-remote-repo-on-github"></a>Vytvoření vzdáleného úložiště na GitHubu

Následující příklad používá hostitele GitHub, ale můžete použít libovolného hostitele Git pro správu verzí v Visual Studio pro Mac.

Chcete-li nastavit úložiště Git, proveďte následující kroky:

1. Vytvořte nové úložiště Git na adrese github.com:

    ![Vytvořit nové úložiště Git](media/version-control-git1-sml.png)

2. Nastavte název, popis a ochranu osobních údajů úložiště. **Neinicializujte** úložiště. Nastavte gitignore a licenci na žádné:

    ![Nastavení podrobností úložiště Git](media/version-control-git2.png)

3. Další stránka vám nabídne možnost zobrazit a zkopírovat adresu protokolu HTTPS nebo SSH do úložiště, které jste vytvořili:

    ![Zobrazit a zkopírovat adresu](media/version-control-git3.png)

   K ukázání Visual Studio pro Mac do tohoto úložiště budete potřebovat adresu HTTPS.

## <a name="publishing-an-existing-project"></a>Publikování existujícího projektu

Máte-li existující projekt, který ještě _není_ ve správě verzí, postupujte podle následujících kroků a nastavte ho v Gitu:

1. Vyberte název řešení z Oblast řešení v Visual Studio pro Mac.

2. V řádku nabídek vyberte možnost Správa **verzí > publikovat v řízení verze** , aby se zobrazilo dialogové okno **úložiště klonování** :

    ![Spustit registraci v Visual Studio pro Mac](media/version-control-git4.png)

    Pokud se tato položka nabídky v nabídce zobrazuje šedě, ujistěte se, že jste vybrali název řešení.

3. Zvolte kartu **vybrat z registrováno** a stiskněte tlačítko **Přidat** :

    ![Přidejte dialogové okno registrované úložiště.](media/version-control-git5.png)

4. Zadejte název úložiště tak, jak chcete, aby se zobrazil místně, a vložte adresu URL z kroku #3. Dialogové okno Konfigurace úložiště by mělo vypadat podobně jako v následujícím příkladu. Stiskněte OK:

    ![Dialogové okno pro zadání podrobností Git](media/version-control-git6.png)

    K připojení k Gitu je taky možné použít SSH.

5. Chcete-li se pokusit o publikování aplikace do Gitu, vyberte úložiště a ujistěte se, že jsou dokončená pole **název modulu** a text **zprávy** :

    ![Pokus o publikování projektu do Gitu](media/version-control-git7.png)

6. Klikněte na **OK**a pak na **publikovat** v dialogovém okně Výstraha.

7. V okně **pověření Git** zadejte svoje uživatelské jméno a heslo GitHubu. 

> [!NOTE]
> Pokud má váš účet povolené dvojúrovňové ověřování (2FA), budete muset vytvořit přístupový token, který se používá místo hesla. Pokud jste přístupový token nevytvořili, postupujte podle kroků v dokumentaci [k přístupovému tokenu](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) Git.

8. Zadejte uživatelské jméno a osobní přístupový token a stiskněte **OK**:

    ![Zadejte uživatelské jméno a heslo pro Git.](media/version-control-git9-sml.png)

9. Po několika sekundách by se mělo řešení publikovat s jeho prvotním potvrzením. Potvrďte, že byla publikována, procházením položky nabídky správy verzí, která by nyní měla být naplněna mnoha možnostmi:

    ![Nabídka správy verzí](media/version-control-git10.png)

10. Po zahájení provádění dalších změn nejprve použijte **řízení verze > nabídce revize a potvrzení** pro otevření zobrazení stavu. Po výběru a potvrzení změn vyberte **Odeslat** a nahrajte změny do vzdáleného úložiště. To umožní všem příslušným uživatelům, aby si ji mohli zobrazit na github.com:

    ![Doručovat změny do vzdáleného úložiště](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Publikování nového projektu

Dialogové okno Nový projekt lze použít k vytvoření nového projektu s místním úložištěm Git. Pokud ho chcete povolit, zaškrtněte políčko **použít Git pro správu verzí** , jak je znázorněno na následujícím snímku obrazovky. Tím dojde k inicializaci úložiště a přidání volitelného souboru. gitignore:

![Vytvořit nový projekt s podporou Gitu](media/version-control-git-publish-new1.png)

Pomocí následujících kroků Nahrajte nové místní úložiště do nového úložiště GitHub:

> [!NOTE]
> Pokud jste ještě nevytvořili úložiště GitHubu, přečtěte si část [vytvoření vzdáleného úložiště na GitHubu](#creating-a-remote-repo-on-github) .

1. Vytvořte své první potvrzení tak, že v řádku nabídek přejdeme na **řízení verze > kontrola a potvrzení** .

2. Na kartě stav vyberte **Potvrdit** v levém horním rohu.

3. Napište potvrzovací zprávu, třeba First Commit, a pak klikněte na **potvrzení změn**:

    ![Potvrdit počáteční změny v úložišti Git](media/version-control-git-publish-new2.png)

4. Dále v řádku nabídek přejděte na Správa **verzí > spravovat větve a vzdálené**části.

5. Přejděte na kartu **vzdálené zdroje** a pak klikněte na **Přidat**.

6. V okně **vzdálené zdroje** přidejte podrobnosti o dříve vytvořeném úložišti GitHub a klikněte na **OK**:

    ![Konfigurace vzdálených zdrojů pro úložiště Git](media/version-control-git-publish-new3.png)

7. Zavřete okno **Konfigurace úložiště Git** a potom v řádku nabídek přejděte na správa **verzí > nabízených změn**.

8. V okně **push do úložiště** klikněte na tlačítko **nabízené změny** :

    ![Odeslat změny do vzdáleného úložiště](media/version-control-git-publish-new4.png)

9. Po zobrazení výzvy zadejte uživatelské jméno a heslo GitHubu.

> [!NOTE]
> Pokud má váš účet povolené dvojúrovňové ověřování (2FA), budete muset vytvořit přístupový token, který se používá místo hesla. Pokud jste přístupový token nevytvořili, postupujte podle kroků v dokumentaci [k přístupovému tokenu](https://help.github.com/articles/creating-an-access-token-for-command-line-use/) Git.

Visual Studio pro Mac nyní vloží změny do vzdáleného úložiště GitHub:

![Potvrzení úspěšného dokončení operace push](media/version-control-git11.png)

## <a name="clone-an-existing-repository"></a>Klonovat existující úložiště

Je možné, že budete muset pracovat s úložištěm GitHub, které existuje jenom na vzdáleném, ne na vašem místním počítači. Visual Studio pro Mac umožňuje rychlé naklonování tohoto úložiště. Pomocí následujících kroků naklonujte tento počítač do počítače:

1. V řádku nabídek vyberte možnost Správa **verzí > úložiště klonování**:

2. Zobrazí se karta **připojit s adresou URL** :

    ![Karta připojit s adresou URL s zadanými podrobnostmi](media/version-control-git13.png)

3. Na stránce GitHub na vzdáleném úložišti stiskněte tlačítko **klonovat nebo stáhnout** a zkopírujte poskytnutou adresu URL:

    ![zobrazená adresa URL GitHubu](media/version-control-git14.png)

4. V poli pro zadání **adresy URL** na kartě **připojit k adrese** URL nahraďte veškerý text. Tím se na této kartě naplní většinu dalších polí, jak je znázorněno na obrázku v kroku #2.

5. Zadejte adresář, do kterého chcete klonovat úložiště, a stiskněte **klon**.

> [!NOTE]
> Pokud je úložiště větší než 4 GB, může docházet k problémům.

## <a name="troubleshooting"></a>Řešení potíží

Pokud máte problémy s inicializací projektu s prázdným vzdáleným úložištěm, můžete vyzkoušet následující postup:

1. Přejít do složky řešení.
1. Stiskněte **příkaz + Shift +.** Chcete-li zobrazit skryté soubory a složky.
1. Pokud je složka **. Git** , odstraňte ji.
1. Pokud existuje soubor **gitignore** , odstraňte ho.
1. Stiskněte **příkaz + Shift +.** skrytí souborů a složek.
1. Otevřete své řešení v sadě VS pro Mac.
1. Na panelu řešení vyberte uzel řešení.
1. Přejděte do nabídky Správa verzí a v části **Správa verzí vyberte publikovat**.
1. Postupujte podle kroků v předchozím kurzu počínaje krokem 6.

## <a name="see-also"></a>Viz také

- [Správa verzí v aplikaci Visual Studio (ve Windows)](/visualstudio/version-control/)
