---
title: Práce s úložištěm Subversion
description: Použití podverze v Visual Studio pro Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 2400ED9C-6236-4C0A-A3AB-9D7CBE1F0CF4
ms.openlocfilehash: bd46a9eba7770b73425f1461fab6cb8443ace26c
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402267"
---
# <a name="working-with-subversion"></a>Práce s úložištěm Subversion

Podverze je centralizovaný systém správy verzí, který umožňuje rezervovat jedinou hlavní kopii centralizovaných dat. Na rozdíl od Gitu, při rezervaci úložiště podverze neklonuje celé úložiště, pouze snímek v daném okamžiku.

Dílčí verze používá model kopírování s úpravou, který umožňuje uživatelům pracovat současně na stejném úložišti. To znamená, že každý uživatel vytvoří místní, nebo pracovní kopii centralizovaných dat, které pracují nezávisle. Změny v pracovních kopiích uživatelů jsou sloučeny chronologicky.

Představte si například, že uživatel a a uživatel B si vyžádají kopii ze vzdáleného úložiště a jednotlivé soubory upraví. Uživatel A provede úpravy a potvrdí je vzdáleně. Předtím, než uživatel B potvrdí svoji práci, musí aktualizovat svou pracovní kopii o změny ze vzdáleného, sloučení změn provedených uživatelem A.

Následující části popisují, jak lze podverze použít pro správu verzí v Visual Studio pro Mac.

Následující obrázek znázorňuje možnosti poskytované Visual Studio pro Mac položkou nabídky správy verzí:

![Položky nabídky správy verzí](media/version-control-svnVersionControlMenu.png)

## <a name="checkout"></a>Rezervace...

Než začnete používat vzdálené úložiště podverze, Projděte si úložiště a vytvořte pracovní kopii tohoto adresáře na místním počítači.

Pokud se chcete dozvědět o používání funkce **registrace** v Visual Studio pro Mac, postupujte podle kroků uvedených v části [Nastavení úložiště podverze](set-up-subversion-repository.md) .

## <a name="update-solution"></a>Aktualizovat řešení

Pokud používáte vzdálené úložiště, je důležité si uvědomit, že ostatní uživatelé můžou upravovat soubory, takže vaše pracovní kopie je zastaralá. Při předvídání konfliktů vždycky doporučujeme, abyste před zahájením práce a před potvrzením načetli všechny změny z úložiště do vašeho řešení. Chcete-li provést změny pro vyžádání obsahu, vyberte položku nabídky pro **kontrolu verzí > aktualizovat řešení** .

## <a name="review-solution-and-commit"></a>Zkontrolovat řešení a potvrdit změny

Chcete-li zkontrolovat změny v souborech, použijte karty změny, viny, protokol a sloučení v každém dokumentu, jak je znázorněno na následujícím obrázku:

![Karty správy verzí](media/version-control-vcTabs.png)

Zkontrolujte všechny změny v projektu procházením **ovládacího prvku verze > revize položky nabídky řešení a potvrzení** :

![Zkontrolovat řešení](media/version-control-vcStatus.png)

To umožňuje zobrazit všechny změny v každém souboru projektu s možností vrátit se, vytvořit opravu nebo potvrdit.

Pokud chcete soubor potvrdit do vzdáleného úložiště, stiskněte potvrdit..., zadejte potvrzovací zprávu a potvrďte ji tlačítkem potvrdit změny:

![Potvrzení souboru](media/version-control-svnCommit.png)

Tato akce odešle změny do úložiště, kde vytvoří novou revizi všech úprav.

## <a name="see-also"></a>Viz také

- [Nastavení úložiště podverze](set-up-subversion-repository.md)
