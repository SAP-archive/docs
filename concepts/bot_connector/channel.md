---
layout: concept
title: Channel
permalink: /concepts/channel
---

The Bot Connector API gives you access to the richest features of the largest number of messaging channels.
This comparison grid provides a comprehensive view of features supported across all available channels.

If a channel doesn't natively support a rich format, Bot Connector will handle it and rewrite the content to have a readable message everywhere.

<table className="mb3" style={{ width: '100%' }}>
  <thead>
    <tr>
      <th width="25%" />
      {supportedChannels.map(el => (
        <th key={el.type} width="50px" style={{ textAlign: 'center' }}>
          {el.logoProps ? (
            <i {...el.logoProps} />
          ) : (
            <img
              className="custom mx-auto mb1"
              src={el.type === 'microsoft' ? el.logo[0] : el.logo}
              width="30px"
              alt=""
            />
          )}
        </th>
      ))}
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Text</td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
    </tr>
    <tr>
      <td>Image/Gif</td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled " />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
    </tr>
    <tr>
      <td>Card</td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
    </tr>
    <tr>
      <td>Carousel</td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
    </tr>
    <tr>
      <td>Buttons</td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
    </tr>
    <tr>
      <td>Quick Replies</td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
    </tr>
    <tr>
      <td>List</td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-blue-500 ion-checkmark-circled" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
      <td className="center">
        <i className="c-grey-400 ion-close" />
      </td>
    </tr>
  </tbody>
</table>
