一：
```cpp
#include <QGraphicsItem>
#include <QPainter>

class CircleItem : public QGraphicsItem
{
public:
    explicit CircleItem(QGraphicsItem *parent = nullptr)
        : QGraphicsItem(parent), m_radius(50), m_color(Qt::red) {}

    QRectF boundingRect() const override {
        return QRectF(-m_radius, -m_radius, m_radius * 2, m_radius * 2);
    }

    void paint(QPainter *painter, const QStyleOptionGraphicsItem *option, 
               QWidget *widget = nullptr) override {
        Q_UNUSED(option);
        Q_UNUSED(widget);
        
        painter->setRenderHint(QPainter::Antialiasing);
        
        // 绘制填充圆形
        painter->setBrush(m_color);
        painter->setPen(QPen(Qt::black, 2));
        painter->drawEllipse(boundingRect());
        
        // 可选：添加一些装饰
        painter->setBrush(Qt::white);
        painter->drawEllipse(QRectF(-m_radius/3, -m_radius/3, m_radius/1.5, m_radius/1.5));
    }

    void setColor(const QColor &color) {
        m_color = color;
        update();
    }

    void setRadius(qreal radius) {
        prepareGeometryChange();
        m_radius = radius;
        update();
    }

private:
    qreal m_radius;
    QColor m_color;
};

```