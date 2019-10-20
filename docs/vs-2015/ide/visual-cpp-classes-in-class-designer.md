---
title: Třídy C++ vizuálu v Návrhář tříd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4fc312736508a11d43cadf789b08aae77c528d35
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72608682"
---
# <a name="visual-c-classes-in-class-designer"></a>Třídy jazyka Visual C++ v návrháři tříd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Návrhář tříd podporuje C++ třídy a vizualizuje nativní C++ třídy stejným způsobem jako obrazce Visual Basic a vizuální C# třídy, s výjimkou toho C++ , že třídy mohou mít více vztahů dědičnosti. Můžete rozbalit obrazec třídy a zobrazit tak více polí a metod ve třídě nebo ho sbalit tak, aby ušetřilo místo.

> [!NOTE]
> Návrhář tříd nepodporuje sjednocení (speciální typ třídy, ve které je přidělená paměť pouze ta, která je potřebná pro největší datový člen sjednocení).

## <a name="simple-inheritance"></a>Jednoduchá dědičnost
 Když přetáhnete více než jednu třídu do diagramu tříd a třídy mají vztah dědičnosti třídy, připojí se k ní šipka. Šipka směřuje do směru základní třídy. Například pokud jsou následující třídy zobrazeny v diagramu tříd, je připojena šipka, ukazující od B do:

```
class A {};
class B : A {};
```

 Můžete také přetáhnout pouze třídu B do diagramu tříd, kliknout pravým tlačítkem myši na obrazec třídy pro B a potom kliknout na tlačítko **Zobrazit základní třídy**. Tím se zobrazí základní třída: A.

## <a name="multiple-inheritance"></a>Vícenásobná dědičnost
 Návrhář tříd podporuje vizualizaci vztahů dědičnosti s více třídami. *Vícenásobná dědičnost* se používá v případě, že odvozená třída má atributy více než jedné základní třídy. Následuje příklad vícenásobné dědičnosti:

```
class Bird {};
class Swimmer {};
class Penguin : public Bird, public Swimmer {};
```

 Když přetáhnete více než jednu třídu do diagramu tříd a třídy mají vztah dědičnosti s více třídami, připojí se šipka. Šipka směřuje do směru základních tříd.

 Klikněte pravým tlačítkem myši na obrazec třídy a potom kliknutím na možnost **Zobrazit základní třídy** zobrazíte základní třídy pro vybranou třídu.

> [!NOTE]
> Příkaz **Zobrazit odvozené třídy** není pro C++ kód podporován. Odvozené třídy můžete zobrazit tak, že kliknete na Zobrazení tříd, rozbalíte uzel typu, rozbalíte podsložku **odvozené typy** a přetáhnete tyto typy do diagramu tříd.

 Další informace o dědičnosti více tříd naleznete v tématu [(NOTINBUILD) vícenásobná dědičnost](https://msdn.microsoft.com/3b74185e-2beb-4e29-8684-441e51d2a2ca) a [více základních tříd](https://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740).

## <a name="abstract-classes"></a>Abstraktní třídy
 Návrhář tříd podporuje abstraktní třídy (také s názvem "abstraktní základní třídy"). Jedná se o třídy, které nikdy nevytváříte, ale ze kterých můžete odvodit jiné třídy. Pomocí příkladu z "vícenásobná dědičnost" dříve v tomto dokumentu můžete vytvořit instanci `Bird` třídy jako jednotlivé objekty následujícím způsobem:

```
int main()
{
   Bird sparrow;
   Bird crow;
   Bird eagle;
}
```

 Nicméně nebudete mít v úmyslu vytvořit instanci `Swimmer` třídy jako jednotlivé objekty. Je možné, že máte v úmyslu odvodit jenom jiné typy tříd zvířat, například `Penguin`, `Whale` a `Fish`. V takovém případě byste třídu `Swimmer` deklarovali jako abstraktní základní třídu.

 Chcete-li deklarovat třídu jako abstraktní, můžete použít klíčové slovo `abstract`. Členy označené jako abstraktní nebo zahrnuté do abstraktní třídy jsou virtuální a musí být implementované třídami odvozenými z abstraktní třídy.

```
class Swimmer abstract
{
   virtual void swim();
   void dive();
};
```

 Můžete také deklarovat třídu jako abstraktní zahrnutím alespoň jedné čistě virtuální funkce:

```
class Swimmer
{
   virtual void swim() = 0;
   void dive();
};
```

 Když zobrazíte tyto deklarace v diagramu tříd, název třídy `Swimmer` a její čistě virtuální funkce `swim` jsou zobrazeny v kurzívě v nadřazeném tvaru třídy spolu s **abstraktní třídou**Notation. Všimněte si, že obrazec typu abstraktní třídy je stejný jako u regulární třídy s tím rozdílem, že jeho ohraničení je tečkovaná čára.

 Třída odvozená z abstraktní základní třídy musí přepsat každou čistě virtuální funkci v základní třídě, jinak nelze vytvořit instanci odvozené třídy. Takže pokud například odvodit třídu `Fish` z `Swimmer` třídy, `Fish` musí přepsat `swim` metoda:

```
class Fish : public Swimmer
{
   void swim(int speed);
};

int main()
{
   Fish guppy;
}
```

 Při zobrazení tohoto kódu v diagramu tříd Návrhář tříd nakreslí čáru dědičnosti z `Fish` na `Swimmer`.

## <a name="anonymous-classes"></a>Anonymní třídy
 Návrhář tříd podporuje anonymní třídy. *Anonymní typy tříd* jsou třídy deklarované bez identifikátoru. Nemohou mít konstruktor nebo destruktor, nemohou být předány jako argumenty funkcím a nemohou být vráceny jako návratové hodnoty z funkcí. Můžete použít anonymní třídu k nahrazení názvu třídy názvem typedef, jak je uvedeno v následujícím příkladu:

```
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

 Struktury můžou být taky anonymní. Návrhář tříd zobrazuje anonymní třídy a struktury stejné, jako zobrazuje příslušný typ. I když můžete deklarovat a zobrazit anonymní třídy a struktury, Návrhář tříd nebude používat název značky, který zadáte. Bude použit název, který Zobrazení tříd generuje. Třída nebo struktura se zobrazí v Zobrazení tříd a Návrhář tříd jako element s názvem **__unnamed**.

 Další informace o anonymních třídách naleznete v tématu [anonymní typy tříd](https://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8).

## <a name="template-classes"></a>Třídy šablon
 Návrhář tříd podporuje vizualizaci tříd šablon. Jsou podporovány vnořené deklarace. V následující tabulce jsou uvedeny některé typické deklarace.

|Element kódu|Zobrazení Návrhář tříd|
|------------------|-------------------------|
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> Template – třída|
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Template – třída|
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> Template – třída|
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Template – třída|

 V následující tabulce jsou uvedeny některé příklady částečné specializace.

|Element kódu|Zobrazení Návrhář tříd|
|------------------|-------------------------|
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Template – třída|
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Template – třída|
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Template – třída|
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Template – třída|

 V následující tabulce jsou uvedeny některé příklady dědičnosti v částečné specializaci.

|Element kódu|Zobrazení Návrhář tříd|
|------------------|-------------------------|
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Template – třída<br /><br /> `B`<br /><br /> Třída<br /><br /> (odkazuje na třídu A)<br /><br /> `C`<br /><br /> Třída<br /><br /> (odkazuje na třídu A)|

 V následující tabulce jsou uvedeny některé příklady funkcí šablon částečné specializace.

|Element kódu|Zobrazení Návrhář tříd|
|------------------|-------------------------|
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> Func \<T, U > (+ 1 přetížení)|
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Template – třída<br /><br /> `B<T2>`<br /><br /> Template – třída<br /><br /> (B je obsaženo v třídě A v rámci **vnořených typů**)|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Třída<br /><br /> -> C \<int ><br /><br /> `C<T>`<br /><br /> Template – třída|

 V následující tabulce jsou uvedeny některé příklady dědičnosti šablon.

|Element kódu|Zobrazení Návrhář tříd|
|------------------|-------------------------|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Třída<br /><br /> – > B<br /><br /> `C<int>`<br /><br /> Třída<br /><br /> (B je obsaženo v třídě C v rámci **vnořených typů**)<br /><br /> `C<T>`<br /><br /> Template – třída|

 V následující tabulce jsou uvedeny některé příklady kanonického specializovaného připojení třídy.

|Element kódu|Zobrazení Návrhář tříd|
|------------------|-------------------------|
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Třída<br /><br /> -> C \<int ><br /><br /> `C<int>`<br /><br /> Třída<br /><br /> `C<T>`<br /><br /> Template – třída<br /><br /> `D`<br /><br /> Třída<br /><br /> -> C \<float >|
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> minimální \<T >|

## <a name="see-also"></a>Viz také
 [Práce s třídami Visual C++ Code (návrhář tříd)](../ide/working-with-visual-cpp-code-class-designer.md) [a strukturami](https://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873) [typu anonymní třídy](https://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8) [(NOTINBUILD) vícenásobná dědičnost](https://msdn.microsoft.com/3b74185e-2beb-4e29-8684-441e51d2a2ca) – [vícenásobné šablony základních tříd](https://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740) [](https://msdn.microsoft.com/library/90fcc14a-2092-47af-9d2e-dba26d25b872)
