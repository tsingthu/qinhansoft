Fragment面试详解.md
# 1.Fragment为什么被称为第五大组件

## 1.1 Fragment为什么被称为第五大组件
Fragment是不属于四大组件的，它有自己的生命周期，并且能够灵活的加入到Activity中去，所以，Fragment被称作第五大组件。
Fragment虽然有自己的生命周期，但是它必须依附于Activity。

## 1.2 Fragment加载到Activity的两种方式
> 1.添加Fragment到Activity的布局文件当中。
> 2.动态在Activity中添加Fragment。

## 1.3 FragmentPagerAdapter与FragmentStatePagerAdapter的区别
#### FragmentStatePagerAdapter：

    destroyItem(){
        // ...
        mCurTransacion.remove(fragment);
    }
释放了内存。
#### FragmentPagerAdapter：

    destroyItem() {
        // ...
        mCurTransacion.detach((Fragment)object);
    }
并没有真正销毁Fragment，即Fragment仍然存在在内存中。

所以，FragmentPagerAdapter更适合页面较少时使用，而FragmentStatePagerAdapter更适合页面较多时使用。

# 2.Fragment的生命周期

# 3.Fragment之间的通信

## 3.1 Fragment与Activity之间的通信
在Fragment中调用Activity中的方法：getActivity()
## 3.2 Fragment与Fragment之间的通信
在Fragment中调用Fragment中的方法：getActivity().findFragmentById()
## 3.3 Activity与Fragment之间的通信
在Activity中调用Fragment中的方法：接口回调

# 4.Fragment管理器：FragmentManager

## replace()
把Activity最上层的Fragment替换为新的Fragment的实例。
## add()
将一个Fragment的实例添加到Activity的最上层。
## remove()
将一个Fragment的实例从Activity中移除。