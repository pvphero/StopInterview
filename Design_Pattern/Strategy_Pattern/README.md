根据极客学院的教程学习总结一下设计模式的内容
### 前言:  
设计模式是遇到问题总结的经验，不是代码，是某类问题的通用设计解决方案
### 目的：  
提高 维护性，扩展性，变化性，复杂度变成O(N)
### 策略模式：  
分别封装行为接口，实现算法组，超类里放行为接口对象，在子类具体定义行为对象。
原则：分离变化部分，封装接口，基于接口编程各种功能。
特点：
同类的行为是可以相互替换的
同级不同类的行为是相互独立
此模式让算法的变化独立于算法的使用者
注意点：
1-分析项目中变化部分和不变部分
2-多用组合少用继承
3-把行为进行类组合，而不是行为的集成
### 场景：  
继承提高的代码的复用性，但是增加子类的复杂度，例如父类增加某些属性，并不是其他子类需要，影响所有子类。
如果把一些行为实现在子类里，又降低代码的复用性。
### 面向对象的问题：  
继承提高的代码的复用性，但是增加子类的复杂度，例如父类增加某些属性，并不是其他子类需要，影响所有子类。
如果把一些行为放在子类里，又降低代码的复用性。
## 结构  
![项目结构](https://img-blog.csdn.net/20180330163146251?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpbnhpbjYxOTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

``` Java
package com.iolo.bc.CeLue.flyBehavior;
/**
 * Created by FengXinXin on 2018/3/30.
 */
public interface FlyBehavior {
    void fly();
}
```
``` Java
package com.iolo.bc.CeLue.flyBehavior;

/**
 * Created by FengXinXin on 2018/3/30.
 */
public class GoodFly implements FlyBehavior{
    @Override
    public void fly() {
        System.out.println("---Good Fly---");
    }
}

```
``` Java
package com.iolo.bc.CeLue.flyBehavior;

/**
 * Created by FengXinXin on 2018/3/30.
 */
public class BadFly implements FlyBehavior{
    @Override
    public void fly() {
        System.out.println("---Bad Fly---");
    }
}

```

``` Java
package com.iolo.bc.CeLue.flyBehavior;

/**
 * Created by FengXinXin on 2018/3/30.
 */
public class NotFly implements FlyBehavior{
    @Override
    public void fly() {
        System.out.println("---Not Fly---");
    }
}

```

``` Java
package com.iolo.bc.CeLue.quackBehavior;

/**
 * Created by FengXinXin on 2018/3/30.
 */
public interface QuackBehavior {
    void quack();
}

```

``` Java
package com.iolo.bc.CeLue.quackBehavior;

/**
 * Created by FengXinXin on 2018/3/30.
 */
public class GoodQuack implements QuackBehavior{
    @Override
    public void quack() {
        System.out.println("~~~Good Quack~~~");
    }
}

```

``` Java
package com.iolo.bc.CeLue.quackBehavior;

/**
 * Created by FengXinXin on 2018/3/30.
 */
public class BadQuack implements QuackBehavior{
    @Override
    public void quack() {
        System.out.println("~~~Bad Quack~~~");
    }
}

```

``` Java
package com.iolo.bc.CeLue.quackBehavior;

/**
 * Created by FengXinXin on 2018/3/30.
 */
public class NotQuack implements QuackBehavior{
    @Override
    public void quack() {
        System.out.println("~~~Not Quack~~~");
    }
}

```

``` Java
package com.iolo.bc.CeLue.duck;

import com.iolo.bc.CeLue.flyBehavior.FlyBehavior;
import com.iolo.bc.CeLue.quackBehavior.QuackBehavior;

/**
 * Created by FengXinXin on 2018/3/30.
 */
public abstract class Duck {
    FlyBehavior mFlyBehavior;
    QuackBehavior mQuackBehavior;

    public Duck() {
    }

    public void Fly() {
        mFlyBehavior.fly();
    }

    public void Quck() {
        mQuackBehavior.quack();
    }

    public void Swim() {
        System.out.println("Swimming------------------");
    }

    public abstract void Display();

    public FlyBehavior getmFlyBehavior() {
        return mFlyBehavior;
    }

    public void setmFlyBehavior(FlyBehavior mFlyBehavior) {
        this.mFlyBehavior = mFlyBehavior;
    }

    public QuackBehavior getmQuackBehavior() {
        return mQuackBehavior;
    }

    public void setmQuackBehavior(QuackBehavior mQuackBehavior) {
        this.mQuackBehavior = mQuackBehavior;
    }
}

```

``` Java
package com.iolo.bc.CeLue.duck;

import com.iolo.bc.CeLue.flyBehavior.GoodFly;
import com.iolo.bc.CeLue.quackBehavior.GoodQuack;

/**
 * Created by FengXinXin on 2018/3/30.
 */
public class GreenDuck extends Duck {

    public GreenDuck() {
        mFlyBehavior = new GoodFly();
        mQuackBehavior = new GoodQuack();
    }

    @Override
    public void Display() {
        System.out.println("This is green duck---");
    }
}

```

``` Java
package com.iolo.bc.CeLue.duck;

import com.iolo.bc.CeLue.flyBehavior.BadFly;
import com.iolo.bc.CeLue.quackBehavior.BadQuack;

/**
 * Created by FengXinXin on 2018/3/30.
 */
public class RedDuck extends Duck {

    public RedDuck() {
        mFlyBehavior = new BadFly();
        mQuackBehavior = new BadQuack();
    }

    @Override
    public void Display() {
        System.out.println("This is red duck---");
    }
}

```

``` Java
package com.iolo.bc.CeLue;

import com.iolo.bc.CeLue.duck.GreenDuck;
import com.iolo.bc.CeLue.duck.RedDuck;
import com.iolo.bc.CeLue.flyBehavior.NotFly;
import com.iolo.bc.CeLue.quackBehavior.NotQuack;

/**
 * Created by FengXinXin on 2018/3/30.
 */
public class Test {
    public static void main(String[] args) {
        GreenDuck greenDuck = new GreenDuck();
        RedDuck redDuck = new RedDuck();
        System.out.println("=============Start==============");
        greenDuck.Display();
        greenDuck.Fly();
        greenDuck.Quck();
        greenDuck.Swim();
        System.out.println("==============================");
        redDuck.Display();
        redDuck.Fly();
        redDuck.Quck();
        redDuck.Swim();
        System.out.println("==============================");
        redDuck.setmFlyBehavior(new NotFly());
        redDuck.setmQuackBehavior(new NotQuack());
        redDuck.Display();
        redDuck.Fly();
        redDuck.Quck();
        System.out.println("=============End==============");
    }
}

```

### 运行结果
![运行结果](https://img-blog.csdn.net/20180330164019738?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpbnhpbjYxOTM=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)